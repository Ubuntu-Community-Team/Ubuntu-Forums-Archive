---
title: "multiple versions of Firefox/Thunderbird required -- howto install ?"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by neandr on 2011-12-26
For Mozilla extension dev/verification I need to work with different versions of FX/TB etc.
That's also because I need to check with nightly builds -- before a new version is released.

Those app version can be found at ftp.mozilla, eg.:
[http://ftp.mozilla.org/pub/mozilla.org/thunderbird/nightly/2011-12-26-03-00-26-comm-aurora/thunderbird-11.0a2.en-US.linux-i686.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/thunderbird/nightly/2011-12-26-03-00-26-comm-aurora/thunderbird-11.0a2.en-US.linux-i686.tar.bz2)

Normally I unpack and move it to /usr/lib/mozilla/.
AFAIK a launcher with /usr/lib/mozilla/thunderbird/thunderbird.sh should start it.
But it doesn't.

Any suggestion?


Xubuntu 11.10, Dell Vostro 3550/64bit

---

### Post by lovinglinux on 2011-12-27
I develop [FoxTester](https://addons.mozilla.org/en-US/firefox/addon/foxtester/) extension. It allows to easily install and launch multiple versions of Firefox, Thunderbird, SeaMonkey and Fennec. Install FoxTester in your main profile only.

---

### Post by neandr on 2011-12-27
Thanks for yr help.

Tried to see how it works with adding that extension to SM 2.4.1.
Unfortunatelly it doesn't install at all!

---

### Post by lovinglinux on 2011-12-27
> **neandr said:**
> Thanks for yr help.

Tried to see how it works with adding that extension to SM 2.4.1.
Unfortunatelly it doesn't install at all!

It only works/install on Firefox. However, it can be used to install/launch SeaMonkey as well.

---

### Post by neandr on 2012-01-07
Only yesterday I was able to install with only limited sucess.
After reading the docu pages (a link to it on the installed extension would be very helpful and saves time for the newbie) I got a setup which downloads the install packages.
Also they are recognized by the extension with install/launch/delete buttons. But using them seems a bit unexpected:

- install will directly prompt with the "installed" buble
- lauch does nothing at all -- beside opening and showing the 'installed' packages with it's icons

Also after today reboot the FoxTester 1.1.7 was disabled, reinstalling the downloaded XPI enabled it again, but how after a new reboot/recheck for extension update?

Basically the idea behind your extension sounds great, but how to get it working smoothly?

Günter

Xubuntu 11.10 / Xfce 4.8
Mozilla/5.0 (Ubuntu; X11; Linux x86_64; rv:8.0) Gecko/20100101 Firefox/8.0
FoxTester1.1.7 [email]foxtester@lovinglinux.megabyet.net[/email]

---

