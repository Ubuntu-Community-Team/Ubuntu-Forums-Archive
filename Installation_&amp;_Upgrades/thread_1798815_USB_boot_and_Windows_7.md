---
title: "USB boot and Windows 7"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by austerus on 2011-07-06
Hello,

I've downloaded Ubuntu 11.04 and used the WIndows tool to create a bootable USB drive on a Corsair 4Gb USB stick.

On my desktop system I run Windows 7.

However, after setting up my ASUSTeK Computer INC. M4A785TD-V EVO (AM3) board to boot exclusively from USB (removed the HDD as an option), my PC still boots directly to Windows 7.

Has anybody encountered this issue? Any ideas on what I could do?

Thanks!

---

### Post by lincoln32 on 2011-07-06
normally on asus you will see a boot option f2 or f12 but if quick boot is enabled in bios it is hard to see I can usually just tap f12 and get lucky
most usb drives will show up as a hdd so with it plugged in look in bios and you should see it listed just under your main hdd just change the order
and make sure if you are using a cd that cd is before hdd's in the boot order then you would not need the f12, I downloaded the manual and it should bios boot option order but have not found the f12 boot option yet
I have seen f12,f2,f10 so keeotrying you will get the combination and I will check back if I find it

---

### Post by lincoln32 on 2011-07-06
also test the usb in another machine it may have failed to install to usb correctly I have seen that a few times

---

### Post by austerus on 2011-07-07
Thanks for the reply!

I tested the USB drive on another PC with Windows XP and it booted as expected, worked nicely.

Another thing that puzzles me is that from the Asus BIOS I disabled the HDD as a boot device, leaving only USB. But strangely enough, after I saved and rebooted, Windows 7 still starts!!

I went back in to make sure I saved my changes and they were saved.

---

### Post by mastablasta on 2011-07-07
no, it seem that certain USB keys and certain motherboards are not compatible for boot.
 
i have similar example. Another patriot USB works fine on both computers so i know both computers can boot from USB well. while my 4Gb toshiba drive works well on one and doesn't boot at all on the other. and i tried everything - reformating, changing the OS. same result.

---

### Post by lincoln32 on 2011-07-07
I noticed there were a lot of bios updates it may be a glitch in bios you might try updating bios and retest and or cd to test what works for boot order,or on older comp I have used Plop at [http://www.plop.at/en/downloads.html](http://www.plop.at/en/downloads.html)   it boots a cd the lets you boot from usb works great forolder computers that did not have a usb boot option
let us know what works so others can do the same.

---

### Post by austerus on 2011-07-07
Solved!

Indeed, I had to deal with drives as seen by the mainboard. I had to choose as #1 my USB drive, but it had to be plugged in during BIOS startup while all my other external drives (2 other) were off.

Unfortunately, now Ubuntu doesn't see my Edimax PCI wireless n card :( but that's another story.

Thanks for all the suggestions guys!

---

