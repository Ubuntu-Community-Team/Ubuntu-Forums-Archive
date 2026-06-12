---
title: "Difficulties installing Ubuntu on Compaq Deskpro"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by PvNugteren on 2005-06-28
Hello!

I've installed Ubuntu on more than one computer, and until now I haven't had any problems during installation. But at the moment I am trying to install 5.04 on an old Compaq Deskpro. I can't find out what specific type of Deskpro it is, but it has a 400 MHz Celeron processor. I have installed sufficient memory (256 Mb).

The problem is, that the installation starts without any problems, until the moment that the first partition is created. The system freezes (progression bar stops at 0%) and the only thing I can do is shut down the system.

Does anybody know why this happens? It's NOT a harddisk problem, I have installed another disk, which works fine in any other computer, and the same thing happens.

Thnx,

Pascal

---

### Post by buellman on 2005-06-28
hi!

maybe your ram has failures? did you check it with memtest or tried other ram?

greets. buellman

---

### Post by PvNugteren on 2005-06-28
Hi buellman,

thanks for the quick reply. I'm pretty sure it's not a ram problem, since I have indeed tried other ram, and according to memtest it works.... Sigh...  Maybe I should just do the right thing and throw the Compaq out on the street ;-)

Thanks,

Pascal

---

### Post by codejunkie on 2005-06-28
[QUOTE=PvNugteren]Hi buellman,

thanks for the quick reply. I'm pretty sure it's not a ram problem, since I have indeed tried other ram, and according to memtest it works.... Sigh...  Maybe I should just do the right thing and throw the Compaq out on the street ;-)

Thanks,

Pascal[/QUOTE]

being a compaq owner i would agree ;-)  but you could try some of the different boot options on the installer like linux acpi=off helped mine also if you have onboard video and an addon video card installed disable the onboard video in the bios if compaq has'nt disabled the option to do so like they have on my motherboard if they have remove the addon video card  switch your monitor over to the onboard video do the install if everything goes ok  and you need the add on video card you can change your xorg.conf to use both cards after the install is complete.

---

### Post by PvNugteren on 2005-06-28
Hi codejunkie and buellman,

it seems I have found the solution, although it's still not clear to me what exactly happened. I did the following:

1. I deleted all partitions on the disk (I don't know how they got there, but there were two partitions already there);

2. During the Ubuntu install, during the partitioning-part, I didn't select "Clear entire disk", but selected the second option. I don't exactly know what the English translation of this option is, but it's something like "Use the biggest uninterrupted free disk space". Sorry for the bad translation, I hope you know what I'm talking about. 

Anyway, after this, it worked like a charm. Maybe it had something to do with Compaq's "unique" (not to say "irritating") system of storing the installer/BIOS on the hard disk (at least, that's what I've been told).  

Thanks,

Pascal

---

### Post by mingus on 2005-06-28
Two common causes of what you encountered are (1) the installer could not safely modify the partition table (corruption) or move as necessary (fragmentation) or (2) there is a hidden partition, usually put there by the manufacturer for recovery or sysadmin.

Also, it is not uncommon for there to be bad filesystem chains or bad sectors (blocks).  By deleting the partitions you would take care of the first, but not the second.  You might want to run e2fsck with the -c option to check this (but read the man page first!).

---

### Post by pandan on 2006-03-02
G'day,
Yeah I've got a Deskpro (don't know what make it is though). My issue it that i can't get the a USB memory stick to work on it.

yeah: sudo mount -t vfat /dev/sda1 /media/usbstick
doesn't work.

Phil.

<edit post 28th Sept 2006>
I found the solution.  It's not ubuntu, it's not the drivers...
It's my inability to check carefully through the BIOS setup.
I only had to disable the BIOS blocking of the USB ports and voila! it works!  silly me ;)

---

### Post by jamesr on 2006-03-02
The default configuration on a Compaq used to be with hidden partition for diagnostics. Even when using Windows on my deskpro's I removed the hidden partition.

---

