---
title: "Firefox tab crashes after upgrade"
date: 2017-11-08
forum: Installation &amp; Upgrades
---

### Post by soundgeek on 2017-11-08
I allowed Lubuntu 14.04.1  to upgrade & this also upgraded Firefox to version 56.

Firefox started fine and would connect to websites, but then often crashed when opening another window or drop-down. I suspected that as this is an old PC (Athlon processor) that it does not support SSE2 features which may be used in the new Firefox release.

I have to stick with an old version of Flash which does not use SSE2.

Perhaps future releases won't run on my PC?

Why can't software sense which hardware features are present & only use those which are available?

Is there a way to install Firefox security updates without feature updates?

I tried installing the latest Opera, but that crashed on launch.

When I installed Firefox ver. 42 the crashes ceased.

---

### Post by Impavidus on 2017-11-08
Software can check for available features of your CPU and avoid if unavailable, but developers can't continue to provide support for old hardware forever. In case of flash, which is proprietary software, when Adobe says you need SSE2 to run flash, you need it. No way around that. An old version may work, but in case of flash running old versions is a bad idea because of security. The good thing is, you rarely need flash nowadays.

Firefox needs SSE2 from verion 53 on. Firefox 52 is an extended support release, which you can download and install from Mozilla directly. That will allow you run firefox on your old processor until June 2018, when support will end.

Using unsupported software may open your computer to security threats, in particular when dealing with web-facing software like web browsers and flash.

Just to make sure this is indeed your problem, try```
cat /proc/cpuinfo | grep sse2
```If that produces no output, your processor doesn't support sse2.

[https://support.mozilla.org/en-US/kb/your-hardware-no-longer-supported](https://support.mozilla.org/en-US/kb/your-hardware-no-longer-supported)

---

### Post by soundgeek on 2017-11-09
All noted.

Impavidus thanks for that test. I'll try it.

Old but working PCs are being made obsolete by the internet. How wasteful!

---

### Post by soundgeek on 2017-11-14
I tried your command. No output.

---

### Post by soundgeek on 2018-01-04
I re-installed an old version of Firefox & I don't get the crashes now.

Is there a way to just load the security updates without changing the version?

---

### Post by #&amp;thj^% on 2018-01-04
> **soundgeek said:**
> I re-installed an old version of Firefox & I don't get the crashes now.

Is there a way to just load the security updates without changing the version?

Make sure you understand what Impavidus has said:
 > Using unsupported software may open your computer to security threats, in particular when **_dealing with web-facing software like web browsers and flash_**.

To Put a package on hold:

```
echo "<package-name> hold" | sudo dpkg --set-selections

```
Remove the hold:

```
echo "<package-name> install" | sudo dpkg --set-selections
```

Display the status of your packages:

```
dpkg --get-selections

```
Display the status of a single package:

```
dpkg --get-selections | grep "<package-name>"

```
I'm assuming you will make the right choice. :)

---

