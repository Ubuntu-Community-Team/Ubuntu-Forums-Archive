---
title: "Installing 12.10"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by MixedUpCody on 2012-11-11
Hey all,

I am trying to install 12.10 on an HP Pavillion g7, and nothing seems to be working correctly. I made ISO disks for 12.10 64-bit and 32-bit, and I even tried 12.04. The results are always the same: when I restart the computer the pubple Ubuntu screen comes up for half a second and then the screen goes black, the drive spins for about 10 minutes (and at one point the Ubuntu drums sound) with the screen black the whole time, and then the computer goes completely silent and the screen remains black. Anyone have any ideas how to fix this? BIOS is set up correctly, and I have installed Ubuntu before (just not on this computer). Thanks for your time, and any help.

Cody

---

### Post by Bashing-om on 2012-11-12
Hi ! Cody; Welcome to the forum.

The black screen is likely a graphics driver issue.
Try booting up with the "nomodeset" option, the guide to do so:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Additional help and info:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

Post back with the results or for additional assistance.
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by MixedUpCody on 2012-11-12
Bashing,

The nomodoset helped a little, now I can see it installing, and it runs for about five minutes with the Ubuntu logo, and the dots indicating progress. But after that the screen goes black again and it just sits there until I restart it. Any ideas?

---

### Post by Mark Phelps on 2012-11-12
Had a similar problem and added "rootdelay=90" to the kernel parms (same place you add nomodeset).  IF that works, you can then try reducing the delay.  I found the lowest I could go and still get a desktop was "45".

---

### Post by MixedUpCody on 2012-11-12
Mark,

I just added nomodoset from the f6 menu on the install screen, there is no root delay option there. Is there a way to do it other than that? Thank you for your help.

Cody

---

### Post by Bashing-om on 2012-11-12
when you choose the f6 option, right -under-left of the (f6)window is the kernel boot command line. enter mark's term at the end of that line.
and f10 to continue the boot.

let us know what results. ==> BDQ

---

### Post by MixedUpCody on 2012-11-12
Okay, I got the problem solved. It was a graphics card issue. I had to go into grub and add "i915.modeset =0" after the splash line. Thank you very much to everyone for your help.

Cody

---

