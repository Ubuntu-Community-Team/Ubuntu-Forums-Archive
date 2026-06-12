---
title: "Installing latest Firefox release in 8.04"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by atravnic on 2010-04-08
Hi folks -- Downloaded Firefox 3.6 (or whatever the latest release is) but can't figure out how to install it. Don't know if this would be a new installation or just an upgrade. Tried Add/Remove and apt-get, but I'm probably doing something wrong. Besides, I'm not a major techie. Can someone please point me.

By extension, I've been running on whatever version of OpenOffice that comes with 8.04 and not getting automatic upgrades. Same question here, how do I get and install it?

Thanks for helping.        ...Fred

---

### Post by Slim Odds on 2010-04-08
> **atravnic said:**
> Hi folks -- Downloaded Firefox 3.6 (or whatever the latest release is) but can't figure out how to install it. Don't know if this would be a new installation or just an upgrade. Tried Add/Remove and apt-get, but I'm probably doing something wrong. Besides, I'm not a major techie. Can someone please point me.

By extension, I've been running on whatever version of OpenOffice that comes with 8.04 and not getting automatic upgrades. Same question here, how do I get and install it?

Thanks for helping.        ...Fred

By far, your best bet is to wait until the end of April and upgrade to 10.04. Then you'll get all of the latest stuff.

---

### Post by 1999panos on 2010-04-08
To upgrade firefox, you have to upgrade Ubuntu to a newer version (9.10 is the latest). 

**To upgrade:**
1) you open update manager from System>Administration>Update Manager.
2) If you have any updates, download & install them.
3) Then do a "Check for updates".
4) Logically at the top of the window will say "New distribution release "8.10" is available". If yes, click "upgrade" and follow the on-screen instructions. (Do this process 3 times till 9.10)
5) If you don't see that [step 4] you do that:
=> Open System > Administration > Software Sources
  then click "Updates" & under "Release Upgrade" choose "Normal Releases". And open update manager and follow [step 4].

---

### Post by naql on 2010-04-08
You could upgrade by adding the Firefox stable Launchpad PPA to your software sources.

Here is the link: [https://launchpad.net/~mozillateam/+archive/firefox-stable?field.series_filter=hardy]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable?field.series_filter=hardy")

---

### Post by marshmallow1304 on 2010-04-08
If you want to stick with an LTS and still have newer versions of programs, you can add individual PPAs for those programs.  For example, you could add the [firefox-stable PPA]("https://launchpad.net/~mozillateam/+archive/firefox-stable") so you'll always have the latest stable version of Firefox.

---

