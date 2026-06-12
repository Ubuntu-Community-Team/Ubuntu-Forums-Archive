---
title: "problem upgrading ubuntu 12.04 to 14.04 through live usb"
date: 2015-04-10
forum: Installation &amp; Upgrades
---

### Post by acharyakushal on 2015-04-10
i downloaded ubuntu 14.04.1 iso and made live usb through built-in start-up disk creator. my problem is when i select install option after booting with live usb it does not show upgrade option. instead it shows "you have multiple system installed, install alongside system" and "erase entire disk and install ubuntu" and "something else". i just want to upgrade my existing ubuntu installation nothing else. i have dual boot system. win 7 and ubuntu 12.04. ubuntu is installed since beta stage but dont remember exactly. win 7 mbr is default. and configured thorugh easybcd.

off topic. i have huge library of flightgear aircrafts and scenery and data. after upgrading will flightgear work as before? i am confused about it.

---

### Post by westie457 on 2015-04-10
Have you tried booting the 12.04 installation then plugging in the USB stick?

The auto-run prompt should give you a chance to upgrade from there.

---

### Post by acharyakushal on 2015-04-10
yes, i tried but nothing happens when i plug-in the usb stick. also a strange thing is that it also shows partial upgrade failure when upgrading through update manager. i have ubuntu installed on /sda5 and swap partition is /sda6. incase if partitions has anything to do with upgrades.

---

### Post by Impavidus on 2015-04-10
I've never done a release upgrade from the live disk, although I believe it's possible. I either upgrade in-place using the option offered by the update manager or I do a clean install. The last may be faster.

Regarding your other point (and the real reason I replied), your library of aircraft and scenery will still work in the new release. Even better, if you didn't use a PPA for flightgear in 12.04, you've got a very old version by now and the latest aircraft and scenery won't work very well. They will on the newer version offered on 14.04. I keep my aircraft and scenery on a separate partition mounted at /usr/local. This way they survive a clean install and at the same time my root partition cannot be filled up because of too many automatic scenery downloads.

---

### Post by acharyakushal on 2015-04-10
> **Impavidus said:**
> I've never done a release upgrade from the live disk, although I believe it's possible. I either upgrade in-place using the option offered by the update manager or I do a clean install. The last may be faster.

Regarding your other point (and the real reason I replied), your library of aircraft and scenery will still work in the new release. Even better, if you didn't use a PPA for flightgear in 12.04, you've got a very old version by now and the latest aircraft and scenery won't work very well. They will on the newer version offered on 14.04. I keep my aircraft and scenery on a separate partition mounted at /usr/local. This way they survive a clean install and at the same time my root partition cannot be filled up because of too many automatic scenery downloads.

Thanks Impavidus

---

### Post by acharyakushal on 2015-04-10
when i try to upgrade through update manager it always throws an error. 
[LEFT][COLOR=#333333][FONT=monospace]
Could not calculate the upgrade
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]An unresolvable problem occurred while calculating the upgrade.[/FONT][/COLOR][COLOR=#333333][FONT=monospace] This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

one more thing. i have installed ubuntu 12.04 since its beta stage. in installation(something else option) it shows ubuntu 12.04 is installed in /sda5 but it seems in live usb it does not 'identify' ubuntu 12.04 is installed on hard disk and so does not offer to "upgrade the existing installation"
[/FONT][/COLOR][/LEFT]

---

