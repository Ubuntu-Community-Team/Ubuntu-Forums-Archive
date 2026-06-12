---
title: "Confusion between &quot;Try Ubuntu&quot; &amp; What is actually Installed"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by eyeroll on 2012-10-09
New laptop, Lenovo Z585 with an AMD A10 I think.  I boot from a 12.04 Live CD and seems like most things are recognized, builtin webcam, bluetooth, wifi etc.

Looks good.

Go to install - not WUBI - I have dedicated partitions for it - / and swap.  cam works - my ugly mug is presented to me as a login pic - seems like things are ok.  Install completed.

Some issues with Grub - dual boot with windows Windows 7 - but I get by those.

Grub comes up and I try and boot - nomodeset already an option.  Boot hangs on an acpi line...  Go into BIOS and disable bluetooth. Same problem.

Leave BT disabled in bios and need to add acpi=off on the kernel line to boot.... Not having ACPI is not a good thing of course.

I don't understand why the Live CD - with BT on in the bios and no kernel options boots fine and seems to detect everything - maybe not the best graphics drivers loaded - boots fine but an install from the same live CD can't boot without acpi=off..

Any thoughts on how I can get around this ?  I would like BT and acpi functionality.  BTW, tried 12.10 beta 2 as well as acpi=off still required to boot.

Thanks

---

### Post by eyeroll on 2012-10-11
Definite progress !!!

After a lot of searching and reviewing dmesg I noticed some references to microcode not being loaded...

I hunted some more and found a reference to amd-64/microcode.  I installed it in my 12.10 beta 2 laptop to see what would happen.  It installed fine so I shutdown restarted and went back into the bios of the laptop.  I re-enabled bluetooth and for some reason disabled legacy usb..

Then the big test - try to reboot into Ubuntu 12.10 beta 2 - but I did not specify acpi=off....  Some seconds of a purplish screen... then boot goodness !!!  Graphcal login displayed so login I did

battery status was displayed, I did a successful resume and even Bluetooth appeared to be recognized...  I installed cheese - built-in cam wasn't working before - ran it and there I was !!!

Not sure how stable this install will be but so far so good.  Everything - except bluetooth - seemns to work fine.  I can enable bluetooth and make it discoverable but was unable to pair with my 
Android phone - tho I did pair it successfully in Windows 7.

Graphics seemed a little slow/choppy so I installed the Ubuntu repo version of the proprietary video driver as well after being unable to do a manual install/build of the latest beta from AMD.

Video seems good and it looks like I can get very good functionality from the lappy in Ubuntu now. :popcorn:

---

