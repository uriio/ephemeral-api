# uriio Ephemeral URL redirector
Thanks to the **[Physical Web](https://github.com/google/physical-web)**, it is possible for low-powered Bluetooth beacons to broadcast a very short URL, that nearby Android and iOS devices can detect and present to the user, without needing a dedicated app installed (except Chrome in iOS case).

In the past, this required an app to even detect the beacons around you, even less was there a standard protocol to transmit actual URLs inside the advertised data payload. The [Eddystone](https://github.com/google/eddystone) beacon format solved this problem, and scanning for nearby Eddystone-URL beacons is now part of Google Play Services, a core Android system package, which (on any compatible Android 4.4+ device) runs a short beacon scan when the screen is turned on.

If a **URL beacon** is detected, a Google web-service will be used to extract metadata for that page, and a notification is presented back on the device, allowing to open that URL locally in the browser. In short, from this point on you can consider that you have a new user, depending on how well your (progressive? fast? cutting-edge? etc.) web-app landing page make a good first impression..

**uriio.com** is a smart redirector that takes this one step further, by assuring that a scanning device was actually in the proximity of the beacon at the specific time when the URL was obtained from the beacon.

This is accomplished by broadcasting short-lived **ephemeral** URLs (instead of a static one that can be easily spoofed, copied, saved, sent to anyone, or visited after a week). It also has some nice features:
* Smart redirecting: the target URL can be updated without needing to touch the beacon
* Redirector hosted on Google's cloud infrastructure, so Nearby notifications appear ASAP (since the metadata is using a Google service).
* URL timestamp and beacon can be authenticated by the target website.

### Client libraries

#### Android
The [uriio-android](https://github.com/uriio/uriio-android) client library builds upon the Android [beacon broadcasting library](https://github.com/uriio/beacons-android) allowing to create
Ephemeral URL beacons, advertised by an Android 5.0+ device.
**[Beacon Toy](https://play.google.com/store/apps/details?id=com.uriio)** is an Android front-end app that officially uses these libraries.

