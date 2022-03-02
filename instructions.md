# Redux From Scratch

![ReduxDataFlowDiagram-49fa8c3968371d9ef6f2a1486bd40a26.gif](Redux%20From%2038608/ReduxDataFlowDiagram-49fa8c3968371d9ef6f2a1486bd40a26.gif)

If you want, you can read something about [why you should use](https://redux.js.org/tutorials/fundamentals/part-1-overview) Redux, but you mainly use it because Luke says.

1. Start a new react project with the typescript template (don’t use the redux template for now)

```jsx
npx create-react-app redux-training --template typescript
```

1. Add the following packages to your project 

```jsx
yarn add redux
yarn add react-redux
yarn add redux-devtools-extension
```

1. Create a [rootReducer](https://redux-toolkit.js.org/api/createreducer)

```jsx
export type RouterState = {
    // e.g. counter: number
}

export enum ActionTypes {
    // e.g. IncrementCounter = "increment_counter",
}

const initialState = { // e.g. counter: 0 }

function counterReducer(state = initialState, action) {
  switch (action.type) {
    // case 'increment_counter':
    //  return { ...state, value: state.value + 1 }
    default:
      return state
  }
}
```

1. Configure your store and add the [redux devtools extension](https://redux.js.org/usage/configuring-your-store). Also install the [devtools extension](https://chrome.google.com/webstore/detail/redux-devtools/) in Chrome

```jsx
import { composeWithDevTools } from ‘redux-devtools-extension’;
const store = createStore(rootReducer, composeWithDevTools( ));
```

1. Add the redux provider wrapper around your App

```jsx
import { Provider } from 'react-redux'

render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
)
```

1. What a rock-solid setup. You should be all set. Now start by implementing a **simple counter** with the following features:
    - Add a button to increment the counter
    - Add a button to decrement the counter
    - The counter should be handled by using Redux
        - Dispatch action item on click
        - Increment/decrement in the reducer
        - useSelector to get the state

1. Great job, thats a very beautiful counter you built. Next up you are gonna build a **to-do list** with the following features:
    - Add an input field to add todos to your list
    - Provide an option to delete todos
    - Add a search field to query your todo list
        - Use the [reselect](https://github.com/reduxjs/reselect) library, so that your filter logic doesn’t trigger with every render of the component). Tutorial: [https://www.youtube.com/watch?v=KZ6UOUCdyd4](https://www.youtube.com/watch?v=KZ6UOUCdyd4)

**Bonus tasks:**

- Make your search case insensitive
- Implement the reselect memoize function from scratch
- Build another fun add-on