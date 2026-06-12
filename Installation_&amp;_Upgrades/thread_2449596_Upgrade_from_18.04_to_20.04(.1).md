---
title: "Upgrade from 18.04 to 20.04(.1?)"
date: 2020-08-30
forum: Installation &amp; Upgrades
---

### Post by quirinovix on 2020-08-30
Hello.

I still do not receive the notification to upgrade. If i change the option to "any version", it offers me the 20.04. Using "only LTS", offers nothing.
Should i use the "any version" and upgrade to 20.04. Shouldn't it offer 20.04.1?

Thank's.

---

### Post by dino99 on 2020-08-30
it will be indeed the latest version available when you will dist upgrade
[https://linuxconfig.org/how-to-upgrade-ubuntu-to-20-04-lts-focal-fossa](https://linuxconfig.org/how-to-upgrade-ubuntu-to-20-04-lts-focal-fossa)

---

### Post by Impavidus on 2020-08-30
An upgrade to "any version" gives you the next supported version, which is currently 20.04. The .1 doesn't really matter. There is a new live disk .iso called 20.04.1 and when your 20.04 system has all the updates included in the new live disk image, it's also called 20.04.1. A release upgrade automatically gives you the new release with all available updates.

An upgrade to "only LTS" give you an upgrade to the next LTS version, which is also 20.04, exactly the same as when you upgrade to "any version", but the upgrade hasn't been released yet. I don't know what they're waiting for. So you can upgrade, but it may be less reliable then if you wait until the upgrade is officially released.

---

### Post by quirinovix on 2020-08-30
I changed the option to "any version", it offered me the 20.04 and i upgraded it. Ended up with 20.04.1. 
Got some errors while upgrading. Told it was going to run recovery. First boot, i got lots of errors. The next reboot, no more errors.

First:
The upgrade will continiu but the "linux-image-5.4.0-42-generic" package may not be in a work state.
Please consider submitting a bur report. triggers looping, abandoned

Second:
Could not install the upgrades.
The upgrade has aborted. Your system could be in an unusable state. A recovery will now run (dpkg --configure -a)

Then:
Upgrade complete
Upgrade was complete but there were erros during the Upgrade process.

---

