# Events

- If you assign a function to an element's event, it must NOT be invoked during assignment.

- options to addEventListener:

1. `once`, the listener will be removed after it triggers if this is set to true.

2. `capture`, the phase where to handle the event.

3. `passive`, if true, then the handler will not call `preventDefault()`

- Removing an event listener requires the same function. Because functions are objects, hence they always get newly created in memory, therefore we need to extract the function and use the specific function.

- `event.currentTarget` is the element that has the event onto it.

- We can also pass in object handlers as events (could also be classes, but then you'd have to create an instance using new keyword).

- Bubbling: When an event happens on an element, it first runs the handlers on it, then on its parent, then all the way up to other ancestors.

- `event.target` (can be a deeply nested element) is the element that triggered the event, `event.currentTarget` is the element which the handler actually runs on.

- `event.stopPropagation()` will stop the event from keep bubbling up, since the event by default will keep bubble up to the window even.

- Capturing: Means the event goes down to the target element.

- To enable capturing phase, `capture` option of the event listener must be set to true.

- To remove the handler, the remove listener needs the same phase.

- Event delegation: If we have many elements handled in a similar way, then instead of assigning a handler to each of them, we put a single handler on their common ancestor.

- Behavior pattern: Add custom attributes to elements within the element that has the event, and depending on the attribute you can decide what to do when the event gets bubbled up to the element where the handler runs.

- You can create custom events via `new Event(type, [, options])`. Use `dispatchEvent(event)` to trigger the event for an element.

- `event.isTrusted` to tell if events came from real user actions or script-generated ones.

- CustomEvent is like Event, but has another option, `detail`, which can contain any type, an event-dependent value associated with the event.

- In order to be able to use `event.preventDefault()` for custom events, the option `cancelable` must be set to true.
