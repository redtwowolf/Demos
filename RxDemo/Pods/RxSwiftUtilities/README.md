RxSwiftUtilities
======================================
[![CocoaPods Compatible](https://img.shields.io/cocoapods/v/RxSwiftUtilities.svg)](https://img.shields.io/cocoapods/v/RxSwiftUtilities.svg)
[![Carthage Compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![Platform](https://img.shields.io/cocoapods/p/RxSwiftUtilities.svg?style=flat)](http://cocoadocs.org/docsets/RxSwiftUtilities)

## About

Helpful classes and extensions for RxSwift which don't belong in RxSwift core.

## Example App

This repo contains an [Example App](ExampleApp/) with interactive examples.

To use the Example App:

```shell
cd ExampleApp
pod install
```

Open the project located in [`ExampleApp/`](ExampleApp/) with Xcode and build/run it.

## Usage

#### ActivityIndicator

```swift
let signingIn = ActivityIndicator()

let signedIn = loginButtonTap.withLatestFrom(usernameAndPassword)
    .flatMapLatest { (username, password) in
        return API.signup(username, password: password)
            .trackActivity(signingIn)
    }
}

signingIn.asDriver()
    .drive(UIApplication.shared.rx.isNetworkActivityIndicatorVisible)
    .addDisposableTo(disposeBag)
```

## Requirements

* Xcode 8.0
* Swift 3.0

## Installation

### [CocoaPods](https://guides.cocoapods.org/using/using-cocoapods.html)

**Tested with `pod --version`: `1.1.1`**

In your `Podfile`:

```ruby
use_frameworks!

target "YOUR_TARGET_NAME" do
  pod "RxSwiftUtilities"
end
```

Replace `YOUR_TARGET_NAME` and then, in the same directory, run:

```shell
pod install
```

### [Carthage](https://github.com/Carthage/Carthage#installing-carthage)

**Tested with `carthage version`: `0.18`**

Add this to `Cartfile`

```
github "RxSwiftCommunity/RxSwiftUtilities"
```

In the same directory, run:

```shell
carthage update
```

Link/Embed frameworks as explained [here](https://github.com/Carthage/Carthage#adding-frameworks-to-an-application). Besides linking `RxSwiftUtilities`, you will also need to link `RxSwift` and `RxCocoa`.

## Contributing

Help is always appreciated!

```shell
git clone git@github.com:RxSwiftCommunity/RxSwiftUtilities.git
cd RxSwiftUtilities
```
> Or use your own forked repo.

```shell
carthage bootstrap
```
> This is necessary in order to be able to build the framework on its own and run tests.
However, if you prefer, you can instead develop it while it's within another project.

Before submitting a PR, please make sure that the tests pass.
