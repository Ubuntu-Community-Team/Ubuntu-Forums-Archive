---
title: "Reinstall Xubuntu from HD? (no CD drive)"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by elainevdw on 2008-01-16
I have a Vaio PCG-C1XS -- which is a very old laptop that has neither a CD-ROM nor a floppy drive. If I remember right, it's not bootable via USB without particular drivers installed (meaning I can't boot from an external USB CD-ROM or floppy if I reformat the HD). I got it as a hand-me-down and have been using it to experiment with, which has been quite fun. :)

I went ahead and ran a bunch of upgrades on it this weekend, and had a bit of a screensaver snafoo, so the computer reset in the middle of the upgrade. It boots and runs, but it's SUPER DUPER slow, and programs will either randomly not start or shut down in the middle of use. 

So, I would like to reinstall Xubuntu. But, is there a way to do so from the HD? (I'm d/ling the alternate install ISO right now.)

When I originally reformatted it, I had to open up my laptop and my desktop and plug the laptop hard drive into the desktop as a slave, which I'd rather not do this time around!

---

### Post by Partyboi2 on 2008-01-16
One way could be to use [this]("https://help.ubuntu.com/community/Installation/FromLinux")
another way could be to remove your current desktop and replace it with the xubuntu desktop

---

### Post by logos34 on 2008-01-16
or this:
[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

### Post by elainevdw on 2008-01-16
Fantastic! I didn't think of searching "install from partition." Will give it a try tonight. Thank you both so much for the links. :)

---

### Post by elainevdw on 2008-01-19
Okay, I'm running into some problems... I'm hoping it's just because I'm not familiar with partitioning in Ubuntu! I have gparted and qtparted on my computer.

So this is what I have:

Device | File System | Size
/dev/sda1 | ext3 | 10.75 GB
/dev/sda2 | extended | 502.03 MB
/dev/sda5 | linux-swap | 502.00 MB

What I want to do is to add another partition on sda1 of about 750 MB, then load the Xubuntu alternate iso files on there, boot to that partition, then reformat the rest of the computer and install everything from the new partition.

I can't edit any of my partitions because it says they're all mounted.

I can't umount /dev/sda1 because "device is busy." I can't umount /dev/sda2 or /dev/sda5 because they're "not mounted" (even though gparted and qtparted both say I can't edit those partitions because they ARE mounted). 

Any ideas? I'm starting to think that my file systems are seriously corrupt from the computer being rebooted in the middle of updating Ubuntu.......... :confused:

---

### Post by Partyboi2 on 2008-01-19
The partition needs to be unmounted for you to be able to work on. I suggest use gparted live cd and do the changes with that. Also backup all the your file you don' want to lose just in case somthing should go wrong. Hopefully it will all go smoothly for you.



edit: Forget about this advice, I just re read the post and see that you are not able to use a cd

---

### Post by Partyboi2 on 2008-01-19
I dont now if this will work. But you can give it a go if you want.
Start up gparted. then right click on your /swap partiton and select "swap off" then you can resize you swap partition, so decrease the /swap down so that you have enough free space to create a new partition for the alternate cd iso. You may need to use the barebone install method instead if you do not have enough space after shrinking swap. Have a look [here]("http://www.psychocats.net/ubuntu/minimal")
But make sure you still have some allocated to /swap

---

### Post by elainevdw on 2008-01-19
Thanks so much for your help! I started up gparted and tried to swap off sda5. It says, "Cannot allocate memory."

I remember having issues trying to boot from USB when I installed Xubuntu in the first place -- but I think I'm going to give it another shot. The worst that can happen is that I'll have to install it the way I did initially, lol.

---

### Post by elainevdw on 2008-01-20
Okay, this is bringing back bad memories, lol. 

I followed instructions on using syslinux to make the USB bootable and then copying the contents of the ISO onto the USB drive. (It's a 2G, btw.)

I can't set the Sony's BIOS to boot from USB. It's only options are CD-ROM, HD and floppy (it came with a USB floppy drive, but no USB CD-ROM). 

Is there a way to tell Grub to boot from the USB drive? After it starts loading from HD0, the first thing it looks at is SDB. (I assume that's my USB, because it starts flashing while Grub is looking at SDB.) But, it just says "Assuming drive cache: write through" and continues loading from the HD instead of the USB.

Maybe I should look into getting a cheap external CD-ROM for this computer if stuff like this happens often...
Edit: Turns out there's only one bootable CD-ROM for my Sony and it's not close enough to "cheap" for my tastes! :lol:

---

