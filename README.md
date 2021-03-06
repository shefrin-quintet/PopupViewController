# PopupViewController

`UIAlertController` drop in replacement with much more customization

You can literally replace `UIAlertController` by `PopupViewController` and `UIAlertAction` by `PopupAction` and you're done. Does not support Action Sheet for now, just alert mode.

Simple example.

``` Swift
  let alert = PopupViewController(title: "Alert title", message: "Alert message, which can be very long and etc....")
  alert.addAction(PopupAction(title: "Ok", type: .Positive, handler: nil))
  presentViewController(alert, animated: true, completion: nil)
```

Result:

![Dark alert](https://raw.githubusercontent.com/Dimillian/PopupViewController/master/Images/classy.png)

By default it come with a dark theme, but where it become powerful is that you can customize it.

Example:

``` Swift
  var customizable = PopupViewController.Customizable()
  customizable.titleColor = UIColor.blueColor()
  customizable.positiveActionColor = UIColor.redColor()
  customizable.messageColor = UIColor.brownColor()
  customizable.messageFont = UIFont.boldSystemFontOfSize(22)
  customizable.negativeActionColor = UIColor.brownColor()
  customizable.actionsHighlightColor = UIColor.redColor()

  let alert = PopupViewController(title: "Alert title",
                                  message: "Alert message, which can be very long message and all that but nobody will ever read it.",
                                  customizable: customizable)
  alert.blurStyle = .ExtraLight
  alert.addAction(PopupAction(title: "Ok", type: .Positive, handler: nil))
  presentViewController(alert, animated: true, completion: nil)
```

Result:

![Ugly alert](https://raw.githubusercontent.com/Dimillian/PopupViewController/master/Images/ugly.png)

Yes this is very ugly. But you know...

You can also set a static `Customizable`, it'll be re used if you pass no customizable in the `PopupViewController` constructor.

``` Swift
  var alertCustomizable = PopupViewController.Customizable()
  alertCustomizable.titleFont = UIFont.avenirNextBold(17)
  alertCustomizable.messageFont = UIFont.avenirNextRegular(15)
  alertCustomizable.messageColor = UIColor.whiteColor()
  alertCustomizable.alertBorderColor = UIColor.tocDarkSeparatorColor()
  alertCustomizable.actionsSeparatorColor = UIColor.darkGrayProgressColor()
  alertCustomizable.actionFont = UIFont.avenirNextRegular(15)
  alertCustomizable.boldActionFont = UIFont.avenirNextBold(15)
  PopupViewController.sharedCustomizable = alertCustomizable
```
## Todo
* [ ] Action Sheet support
* [ ] UITextFields Support
* [ ] Custom view support
* [ ] Shared Customizable configuration
* [ ] Remove cartography dependency
* [ ] Easier custom transition overwrite
* [ ] Better default transition

## Installation

### Normal

Add `pod 'PopupViewController'` in your podfile and then run `pod install`

### Dev mode

Clone this repository and and run `pod install` in both the PopupViewController and Example directory.

### Note

It use the amazing [Cartography](https://github.com/robb/Cartography) as a dependency for now because I'm a lazy ass and I don't want to look at the Apple doc for the ugly Autolayout code hint.
