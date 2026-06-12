---
title: "Laptop with Two Hard drives"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by inderbir on 2007-06-22
I have 2 hard drives and one has windows vista installed on it while the other one is just a data hard drive (no OS installed on it). I want to install ubuntu on the data hard drive and well my problem comes here since I have a laptop I cant change the wire(hard drive wire) every time I boot the computer to choose what OS I want. So is it possible to dual boot with two hardrives? If so how? Help greatly appreciated.

Also I just read this post:
[http://ubuntuforums.org/showthread.php?t=378933&highlight=dual+boot+two+hard+drives]("http://ubuntuforums.org/showthread.php?t=378933&highlight=dual+boot+two+hard+drives")

and well I understand the two hard drive thing now, but if GRUB installed on the same hard drive as my windows hard drive will it mess up the windows partition, also I have vista and I heard a lot of issues when installing Ubuntu with Vista.

---

### Post by TimelessRogue on 2007-06-22
Hey, inderbir, it's not on my laptop, but I had XP and Ubuntu installed on two separate hard drives (and now Kubuntu on a third) on my desktop with no problems at all with Grub.  Not sure about Vista though.  So the long and short of it is yes, you can install on two separate hard drives and it shouldn't be any more of a problem on a laptop than on my desktop.  And you shouldn't have any problem with Grub either.  But ... I would backup your Vista drive just in case ... and then go for it ...

---

### Post by inderbir on 2007-06-22
O thanks I have one more question should I make a partition on the vista hard drive and install GRUB there or do I install it on the vista partition. The thing I am worried about is that If I make a partition for GRUB on the vista hard drive the computer wont boot up the GRUB partition since it will probably boot the vista partition, does GRUB automatically make its partition the primary boot one? Thanks in advance.

---

### Post by logos34 on 2007-06-22
Personally I would recommend you put grub on the mbr of the data drive (which is where ubuntu is going anyway).  That way you leave vista bootloader alone and all you have to do is change the bios boot order when you want to go into the other OS.  Make sure the ubuntu install target drive is listed first in the BIOS hard disk boot order, that way when you get to the part where grub is installed, it will go to the ubuntu drive because it installs by defualt to '(hd0)'--the first hard drive detected in the bios.  It should also detect vista and add an entry for it in /boot/grub/menu.lst, as well as /etc/fstab (so it automounts in linux).  As for the entry in mneu.lst--you may or may not be able to boot vista from grub menu, even if it gets the mapping all correct.

---

