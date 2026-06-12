---
title: "Ubuntu 10.04 doesn't work on my computer"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by hle on 2010-06-01
Ubuntu 10.04 doesn't seem to work on my computer. When I install it (tried both CD, DVD and USB-stick) all I see is "Ubuntu" with a number of dots underneath, and after a while the screen turns black.
 
I also tried the alternative ISO (with non-graphical interface), and that installation worked; I could partition the HD, enter username and password and it copied all files to the HD. But when it said it was finnished, and I rebooted the computer (without the installation media) "Ubuntu" shows on screen with a nuber of dots underneath, and after a while the screen turns black.
 
The computer is new, has an i5-750 CPU, 4GB RAM and a XFX Radeon 5670 1GB graphics adapter and two identical HD:s, one with a working Windows 7 installation (disconnected when I try installing Ubuntu).
 
Please, HELP!

---

### Post by dino99 on 2010-06-01
try to boot with nomodeset on the boot line

---

### Post by hle on 2010-06-01
How? (sorry, quite new to Ubuntu). I don't get any options when starting the computer, the first thing I see is the purple screen with the dots, and then nothing...

---

### Post by ajgreeny on 2010-06-01
Hit any key as the CD boots and you will get a menu with F key options showing.  You may not find that nomodeset helps, unfortunately, and I imagine you may have an older ati graphics card which seem to be the bugbear of this version of ubuntu.

I got mine running using the UNR version of ubuntu live CD, and then added the things that the UNR version does not have like brasero, compiz, etc by installing ubuntu-desktop.  No idea why that worked better but it did.  My machine now works OK; not quite as good as Jaunty or karmic, but still extremely good.

---

### Post by efflandt on 2010-06-01
If you press any key when you first see some graphics at the bottom of the screen from the boot CD, once you select your language there is an F6 button.  Not sure if that has nomodeset listed.  Otherwise if you press the right cursor arrow, you should be able to add **nomodeset** to the end of the boot line.

Or if you installed a system that gets to the grub menu, from there, you can press "e" and add **nomodeset** to the linux line after **quiet splash**.  Or you might even want to erase the quiet splash (so you can see boot messages) and just use nomodeset in place of that.

See [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by hle on 2010-06-01
Thanks all,
 
I will try what you have suggested as soon as can (far away from that computer right now :(). But I have to admit that I would have hoped that it was as easy installing Ubuntu as Windows 7... But I will not give up!!!

---

