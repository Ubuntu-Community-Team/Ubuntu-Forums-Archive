---
title: "Karmic Doesn't Like My Compaq Presario Laptop w/ ATI Video Adapter"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by Windows Refugee on 2010-01-29
Machine: Compaq Presario 906US laptop
         AMD Athlon 1500+ CPU
         512 MB Ram
         ATI graphics adapter


No problems with Intrepid or Jaunty on this laptop, but after upgrade to Karmic, machine hangs with a blank screen about two seconds after selecting boot choice in Grub.

Alt + F1 brings up a GREEN terminal screen that eventually turns black and boots with a really big font.  Karmic says that it is running in low resolution mode, and I get the error "(EE) no devices detected".

I followed a suggestion to install the "Envy Next Generation" package, which allowed me to download an ATI driver.  While the machine still hangs after exiting Grub, pressing Alt + F1 boots in a terminal window as before, but now I do eventually get to the desktop. (I still get the "(EE) no devices detected" error during boot.) See my other thread on this problem... [http://ubuntuforums.org/showthread.php?t=1389307](http://ubuntuforums.org/showthread.php?t=1389307)

I'm wondering if there are any known problems with Karmic running on machines with ATI graphics adapters, or what else might be causing Karmic to not get along with this laptop.

---

### Post by Windows Refugee on 2010-01-30
Just a thought...

Could the amount of shared system memory that is dedicated to the video adapter (selected in the system BIOS), have anything to do with this problem ?

---

### Post by Mark Phelps on 2010-02-01
> **Windows Refugee said:**
> ... I'm wondering if there are any known problems with Karmic running on machines with ATI graphics adapters, or what else might be causing Karmic to not get along with this laptop.
Yes ... Karmic will not run ATI restricted drivers (no matter HOW you install them) with any of the discontinued ATI cards/chips.

Your only option at this point is to remove the restricted drivers and replace them with the open source drivers.  See the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

