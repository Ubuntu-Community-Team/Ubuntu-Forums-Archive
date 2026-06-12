---
title: "after installation of 11.10 grub error: &quot;no such partition&quot;"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by joom on 2012-03-01
Hi!
I've been searching on this topic and couldn't be helped yet.
I've installed ubuntu 11.10 on a harddisk with a ntfs-partition already on it.
Installation works fine.
After reboot I'm prompted with "grub rescue" and receive the error: no such partition.
Following this guide
[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)
I discovered, that grub is set to the wrong hd,
however, manual booting doesn't work, because when i set grub's parameters "prefix" and "root" to the correct partition, i still cannot install the modules needed for booting.
Whenever I want to install a module i am receiving the error: "unknown filesystem". All partitions are listed as msdos partitions, for example my root is at (hd1,msdos5)
Glad if anyone could help.
btw i tried the alternate install disc, and manual partitioning, too.
i also tried to put /boot on a seperate bootable partition.
nothing worked, though.
also, the ubuntu 11.10 live cd doesn't work on my system. at some point the live cd booting process keeps hanging and is only presenting me with nice background screen.
thx in advance.

---

### Post by KingLewy on 2012-03-01
I am having this exact same problem after tweaking my partitions in GParted. I moved the partition containing the Grub files. Whoops.

After reading the same guide and trying the same methods I still come up with the "unknown filesystem" error. I also cannot find the *linux* and *initrd.img* files, but grub.cfg is where it should be.

I tried reinstalling Grub from a live cd, that hasn't worked.

I too would appreciate a fix.

---

### Post by oldfred on 2012-03-01
This sometimes fixes issues, but run the boot info script and post the link it creates to your results.txt.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Is this an older system? Some old BIOS could only boot from the first 137GB of a drive.

---

### Post by KingLewy on 2012-03-01
I feel pretty silly. Discovered I was pointing grub rescue towards the wrong partition. Still, couldn't make the changes stick and the Boot Repair tool fixed that for me. Great tool. Thanks for your help oldfred :D Good luck joom.

---

### Post by oldfred on 2012-03-01
You can run Boot-Repair also. If you are getting past booting it may not help as many systems need a boot parameter to set video correctly.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

