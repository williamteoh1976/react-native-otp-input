# @twotalltotems/react-native-otp-input

**@twotalltotems/react-native-otp-input** is a tiny JS library which provides an elegant UI for user to input one time passcode (OTP). It handles the input suggestion on iOS when the OTP SMS is received. For Android, it will autofill when you press the copy button on the SMS notification bar. It also features a carefully crafted flow to handle edge cases for volatile user gestures. We provide default UI but you can always customize the appearance as you like.

![demo.gif](https://s3.ca-central-1.amazonaws.com/tttevents/iosvideo.gif)
![demo.gif](https://s3.ca-central-1.amazonaws.com/tttevents/android.gif)

## Installation
`npm install --save @twotalltotems/react-native-otp-input`
or
`yarn add @twotalltotems/react-native-otp-input`

## Dependencies
It does not have additional dependencies except for react native itself.

## Basic Usage

```
import OTPInputView from '@twotalltotems/react-native-otp-input'

<OTPInputView
    style={{width: '80%', height: 200}}
    pinCount={4}
    code=""
    autoFocusOnLoad={true}
    // codeInputFieldStyle={styles.borderStyleBase}
    // codeInputHighlightStyle={styles.borderStyleHighLighted}
    codeInputFieldStyle={styles.underlineStyleBase}
    codeInputHighlightStyle={styles.underlineStyleHighLighted}
    onCodeFilled = {(code => {
        console.log(`Code is ${code}, you are good to go!`)
    })}
/>

const styles = StyleSheet.create({
  borderStyleBase: {
    width: 30,
    height: 45
  },

  borderStyleHighLighted: {
    borderColor: "#03DAC6",
  },

  underlineStyleBase: {
    width: 30,
    height: 45,
    borderWidth: 0,
    borderBottomWidth: 1,
  },

  underlineStyleHighLighted: {
    borderColor: "#03DAC6",
  },
});

```

## Parameters

| Parameter   | required | Description |
|-------------|----------|-------------|
| pinCount    |    YES   |  Number of digits you want |
| code        |    NO    |  Besides providing an initial value, you can also give this value using state or props. It will override the user input and reset the focus. For example, you can use it to hook up with the Android SMS Retriever API. |
| codeInputFieldStyle | NO | The style of the input field which is NOT focused |
| codeInputHighlightStyle | NO | The style of the input field which is focused |
| autoFocusOnLoad | NO | Auto activate the input and bring up the keyboard when component is loaded |
| onCodeFilled | NO | callback when the code is done |

## Notes
The iOS input suggestion requires React Native 0.58+ and works for iOS 12 and above. 

On Android, it will be autofilled when you press the copy code button in the notification bar (see above gif). It will do so  only if the code is sent after the view is loaded. So make sure you request the code AFTER this view is loaded.

If you are interested in Android SMS Retriever API, I would suggest @Faizal's repo [React-Native-OTP-Verify](https://github.com/faizalshap/react-native-otp-verify). It looks pretty cool and it should be straight-forward to use React-Native-OTP-Verify along with this library.

## RoadMap
* [ ] Typescript
* [ ] Add tests

## Developers
The library is developed by Anson Yao, Felipe Peña and other mobile team members in TTT studios.

[TTT studios](https://ttt.studio/) is a software developement agency operating in Vancouver. We craft software in mobile, web, backend, facial recognition, AI, AR/VR. 

![ttt-logo.png](https://ttt.studio/wp-content/themes/tttwordpresstheme/imgs/ttt-colour.png)