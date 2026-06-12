---
title: "Very strange GRUB(?) problem..."
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by chadjohnson on 2007-11-26
My dev server's IDE HDD went bad, so (i/o error on partition 1), so I replaced it with a new one. I reloaded a copy of the MBR using dd (dd if=mbr.dd of=/dev/sda), and then I reimaged using SystemRescueCD the first partition with an image I created with partimage. However, when I rebooted, I got a GRUB 16 error (inconsistent file system).

So, I booted into a Gutsy CD, deleted the partitions, redid the partitioning (with different size partitions), and then reinstalled using a standard Gutsy install. But when I reboot, I STILL get a GRUB 16 error. Some times I get a GRUB 17 error (unable to mount partition). This simply bewilders me.

I even tried reinstalling using the Feisty server CD; same problem.

What could be the problem?? Here are some things I thought of:

[LIST]
[*]Boot sector virus
[*]Bad replacement HDD
[*]Bad hardware (the power had gone out when the night before the problems began, and it did not boot when I got up)
[*]Incorrect jumper settings (but I tried all the options for master (16 heads, 15 heads, 32GB clip))
[*]GRUB bug
[*]GRUB not installed correctly
[*]Incorrect GRUB settings in menu.lst
[*]BIOS virus
[*]Bad BIOS battery
[*]The MBR is screwed (but shouldn't the installers have totally replaced this?)
[/LIST]

Any ideas? Please help! I rely on this thing for work.


**EDIT**

Looking at [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html), the GRUB 16 and 17 errors could also be "Device string unrecognizable" or "Invalid device requested" -- I'm not sure ATM whether it got to stage 2.

Something else I thought of: wrong version of GRUB (but the installers should have replaced this, no? I also ran grub-install).

---

### Post by of_darkness on 2007-11-26
1:make sure of where grub reads menu.lst from if you have som old menu.lst lying around somvare..
2:look at devic.map to make soure of that the partions are showing upp corretly -for me it was saying hda-hdb-sda when it should have bean - sda-sdb-sdc and some times because of a bug the devices jumpes around a litle bit.. sda-->sdc sdc-->sdb etc..

And in menu.lst youse uuid:s of the partions 2 make soure of it points 2 a correkt partion..

3:make soure of that the pointings in menu.lst exist on the location it pionts 2..

---

### Post by chadjohnson on 2007-11-26
Thanks for the response. Everything you mentioned checks out.

---

### Post by chadjohnson on 2007-11-26
bump...*desperate*

---

### Post by torgrot on 2007-11-26
did you try sudo grub find /boot/grub/menu.lst to find out if you have the menu.lst file intact?
or sudo grub geometry to determine if grub sees the disk? see this link for all things grub [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

torgrot

---

### Post by chadjohnson on 2007-11-27
Thanks for the link. I've very carefully went over everything there, and I've already tried everything noted which could be of use.

This is madness. I used DBAN to erase the disk entirely, then I booted into the Feisty i386 server CD and installed that like normal, and when I reboot, the stupid computer just keeps rebooting continuously, right when it starts to load GRUB.

This is just ridiculous. Does it sound like the new hard drive is bad?

---

### Post by chadjohnson on 2007-11-27
Ok, I've made some interesting progress. I took the drive out and put it in my mom's computer (which I should have done a long time ago), and it boots. So apparently there is something wrong with my computer or its configuration. Maybe resetting the BIOS will help.

My computer has no problem booting live CDs, though.

---

### Post by chadjohnson on 2007-11-27
Well hell, I got it to boot with LILO using the instructions here: [http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html](http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html).

The Feisty server installer gave me grief and froze at 50% when installing LILO (bug?). So, I used SystemRescueCD. It would be nice if in the server installer it ASKED whether the user wants to install GRUB or LILO rather than just going ahead with GRUB.

---

### Post by jespdj on 2007-11-27
I sometimes get GRUB error 16, 17 or 18 too. I found somewhere that this might be a problem with specific CD/DVD drives. I have a SATA harddisk and SATA DVD drive.

Things that might help are:

1. In the BIOS settings, make the harddisk the first boot device (not the CD)
2. Plug-in the CD drive on another SATA connector on your motherboard
3. Check if the SATA cables of your harddisk and CD/DVD drive are OK and properly connected

---

