---
title: "Can't run unr 9.1 from usb stick?"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by comethalley on 2010-02-10
So, I'm totally new to ubuntu, and linux in general.  I copied the unr 9.10 iso to my usb stick fine using the program from pendrivelinux for ubuntu 9.1.  I think it worked well, because it now has a ubuntu logo on the usb and says "install ubuntu netbook remix."  When I get to the BIOS menu and to the boot options, I get a box which says three things: SDD slot, D: drive, and disabled (maybe talking about the D:?)  When I press enter on the D: drive nothing happens.  When I say to save configuration and exit it goes right to xp again.  I have no idea what to do... I'm on an EEEpc 1005-HA running xp.

---

### Post by pietpaardebloem on 2010-02-14
I also have an Asus eeepc 1005 ha. and also struggled with booting in the beginning. probably your usb is alright. to get it working probably try this.
-Plug the usb into the computer.
-Switch on the computer
-while starting up hit the esc buton.
-you now get a small menu where you can choose from which device you want to boot.

if xp starts again you were probably too late to hit the esc.

Entering the bios via F2 and try to set the boot sequence I found two possibilities.First when you start the computer without the usb connected. you do what you think is logic. setting the (if I remember well) the removable device first in order. after this you restart with the device en you proably start up windows from the hard drive. this is not what you wanted.
second, if you enter the Bios (f2) with the usb connected you will probably find an extra option under the boot sequence line. in there I found that the computer considers the usb also as a bootable hard drive. listing the bootable drives (your usb and the actual hard drive) with your usb as the second in line. That's why windows keep appearing after every restart. By hitting the esc you choose the simplest way

Good luck

Oh and there is the other small thing. many people find the internal microphone not yet working (the external one is) in 9.10. this is a known problem. as it's a known problem I hope this problem is solved in the next version 10.04. for the rest the asus a nice machine.

---

