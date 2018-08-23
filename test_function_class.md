# Test function class with JEST and sinon

```javascript
export default class cloneButton extends Component {
  constructor(...args) {
    super(...args);
    this. _handleCloneClick = this. _handleCloneClick.bind(this);
  }

  _handleCloneClick() {
    event.preventDefault();
    event.stopPropagation();

    this.props.handleClone(this.props.user.id);
  }

  render() {
    return (<button onClick={this. _handleCloneClick}>Clone</button>);
  }
}
```

```javascript
it('clone should call handleCloneClick when clicked', () => {
  sinon.spy(cloneButton.prototype, '_handleCloneClick');
  const wrapper = mount(<cloneButton/>);
  wrapper.find('#clone-btn').simulate('click');
  expect(spy).toHaveBeenCalled() //adept assertion to the tool you use
});
```
or

```javascript
it('clone should call handleCloneClick when clicked', () => {      
  const wrapper = mount(<cloneButton/>);
  sinon.spy(wrapper.instance(), "_handleCloneClick");
  wrapper.update();
  wrapper.find('#clone-btn').simulate('click');
  expect(spy).toHaveBeenCalled() //adept assertion to the tool you use
});
```
