---
title: "Ubuntu black screen on installation"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by AwTheisen on 2010-09-03
I am currently trying to put the newest version of Ubuntu onto a piece of a computer we got for free, it meets the reqs and all that but i keep running into a blank screen right after the Ubuntu loading screen with teh five red dots at the bottom.  I have tried booting with acpi=off and i915.modeset = 1 and i915.modeset = 0 xforcevesa

to no avail what ever i do i receive a black screen,  I debated downloading the alternate version but i don't have another cd to burn it too, for some reason the computer won't pick up usb boot discs and i have no knowledge in creating one.  any help would be grand, just wanted to get it up and running by today

I installed windows 7 on it today just so we could get something going with it, but i plan on wiping that off while installing ubuntu

---

### Post by davidmohammed on 2010-09-03
what graphics do you have?

Have you tried the boot option "nomodeset"?

---

### Post by AwTheisen on 2010-09-03
Yes i have tried nomodeset, same thing occured, i am trying to install it through windows but it told me to reboot and after reboot it goes back to the ubuntu loading screen and went black, i applied an option this time called safe gui or something of that kind, and it is still running or doing something so well see how that goes, after it either never ends or finally finishes ill check to see what GFX we have i'd like to assume its integrated into the CPU but not positive

im also burning a copy of the alternate version as we speak, i hope it will solve my troubles

---

### Post by davidmohammed on 2010-09-03
sometimes troublesome installs could be due to one piece of equipment e.g. dual graphics cards, two dvd devices, multicard reader etc.

Suggest the following:

open the case of the PC. unplug everything except the bare-essentials - one harddrive connected to the motherboard, one DVD drive and  Connect the onboard graphics (if you have one).  Make sure nothing else is connected.

Try again to install (you may wish to retry each of those boot options again).  Hopefully you'll get to the desktop.  At that point, start plugging in devices one at a time until you find out which device is causing the issue.

---

### Post by AwTheisen on 2010-09-03
Alright well i tried the alternate installer and it cuts to a blue screen with a gray command line after i choose the partition options... any ideas there?
atleast it loads up and lets me input options i've tried multiple partition attempts too and nothing seems to load up after i hit yes perform these partitions

im not planning on going that indepth to take apart the computer just for linux, if all else fails ill just use windows.  sad sad day that will be

---

