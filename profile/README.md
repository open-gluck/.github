# OpenGlück

The OpenGlück project is a collection of free software that can be used to help
build a riche ecosystem of apps and tools for diabetes users.

## Features

- modern iOS and iPadOS app, with full support of iOS 17, Lock Screen widgets, Home Screen widgets
- full support of watchOS 10: you can use any watch face and see your blood glucose in real-time, and if you're lucky to have a Series 9 or Ultra 2, use the new double-tap gesture to instantly show a graph with your recent activity (recent blood glucose, basal insulin shots, snacks in response to lows);
- provides a Catalyst app, for use in macOS, where you can have live widgets and explore recent data.

### Apple Watch

![image](https://github.com/open-gluck/.github/assets/66381046/00f71f7a-d6b5-491d-b175-c8c4f1f37009)

### iPhone

The Lock and Home screens showing available widgets:

![image](https://github.com/open-gluck/.github/assets/66381046/3be96363-f8f6-4d5e-b452-73c0d9b02952)

### iPad

### Mac

TODO

## Pre-Requisites

In order to have OpenGlück work on your iPhone or Apple Watch, you need to set up a few things first:

- the [OpenGlück server](https://github.com/open-gluck/opengluck-server) on a machine that's always on, and ready to accept HTTPS connections (you can use a cheap cloud instance, or a computer at home that's never turned off);
- use an app that's compatible with OpenGlück (see a list below);
- for complications and widgets to actually refresh, you need to enroll in the [Apple Developer Program](https://developer.apple.com/programs/) — this is important so that you can lift restrictions concerning how often WidgetKit widgets are refreshed.

## Compatible Apps

The [OpenGlück server](https://github.com/open-gluck/opengluck-server) is a small piece of software, that's agnostic of which CGM, blood glucose reader, closed loop system or any of your hardware. Instead, if relies on two things:
- its exhaustive API to import and retrieve data;
- its convenient webhooks feature to support for plug-ins to react when things happen (like a new reading, a new insulin shot is recorded, etc.)

Below is a list of supported software:

- [xDrip4iOS](https://xdrip4ios.readthedocs.io/en/latest/) is supported with the following pull request that you need to apply.

## FAQ

### Any creative use of OpenGlück?

Sure, what about these ideas:
- create a plug-in that turn on your smart lights when you're low at night;
- upload all your readings to a Google sheet and make a plug-in that send you weekly reports about how you're doing;
- most of us with a CGM have alerts when they experience a low or high, but what about alerts when back in the normal range? turns out we have a [plugin, `opengluck-webhooks-apns`](https://github.com/open-gluck/opengluck-webhook-apns) that does exactly that;
- and, this list is not over!

### Why do you require enrolling on the Apple Developer Program for full widget/complication functionnality?

Because it's the only way that truly works. 

If, for some reasons, you can't enroll or don't want to enroll, you can still use other features of OpenGlük. Sure, you'll miss real-time widgets and complications, but that's about it. If you need it, we have a complication with just an icon, that launches the app. It's an easy and convenient way to still be able to use OpenGlück, albeit one click away!

Early versions of this software used a hack with a contact photo that was updated whenever the blood glucose change. That's cool but once in a while, the data wasn't being updated, and there was a serious risk of applying a wrong decision because data was simply not up to date. This is the same issue that appears with other software that use similar methods, such as the “calendar” app (though the Contacts app might be more elegant as it visually a circle that's available in more watch faces).

If you're interested, the code for updating the contact photo is still present, feel free to dig with it. Personally I'm not confident it's worth the risk, but I'm always open for discussion.

### Do you need your iPhone to use the Apple Watch app?

No, but your CGM or closed-loop system still might.

But, if you have a cellular Apple Watch, and don't need your phone, you'll be good to go.

### Does OpenGlück support “follower” mode?

Sure, just share the same token (or create another user on the OpenGlück server).

### Why didn't you build up on NightScout/<other alternative>?

OpenGlück is supposed to be a foundation, freeing you from whatever software and hardware you use.

Think about it like an Apple TV: when you own one, you're not stuck to using the set-top-box of your internet provider. Which is good from a consumer standpoint perspective, you can change provider whenever you like and still, use the same friendly interface you're used to. And if your internet provider provides special features that you'll like, you're also free to use them in addition to your Apple TV.

This means that, by design, the OpenGlück server will not have bells and whistles, and will rely on third-parties applications to provide all the features. Of course, if you have an iPhone/iPad/Mac/Apple Watch, you are encouraged to use our app but this is by no means necessary.
