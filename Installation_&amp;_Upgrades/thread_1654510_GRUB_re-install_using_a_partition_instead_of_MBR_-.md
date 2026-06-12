---
title: "GRUB re-install using a partition instead of MBR - why?"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by XEtedBear on 2010-12-28
I'm trying to re-install Grub2 on a dual boot (Win/XP & Ubuntu 10.10) system which will not boot. I am following the guide here:
```

https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows

```

This guide explicitly states that the procedure will re-install GRUB to the Master Boot Record, overwritng whatever is there. However, the final step results in this warning message:

"grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea....."


I guess I agree - that's not what I want to do. Where is the defect in the procedure and how do I overcome it?


If I try alternative advice, available in the forums, by using the command ```
 sudo grub-install /dev/sda 
``` then I receive the error message ```
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?)
```

Looking at the mount command output, I think the required device is mounted. 

How do I recover from this?

---

### Post by Quackers on 2010-12-28
Are you installing grub to a partition? eg sda1, sda3 or sdb2
It should go to sda or sdb ie no partition number.

---

### Post by oldfred on 2010-12-28
Drives are sda, sdb etc. Partitions are parts of a drive so they have numbers at the end - sda1, sda2, sdb1 etc.

You probably mounted your partition with Ubuntu - sda5 but then tried to install grub to sda5 not sda (no number).

---

### Post by BrockStrongo on 2010-12-28
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
this is the best walkthrough I've seen. Make sure the last line of code ends with /sda     when I tried putting a number after sda I got the error that you got. 
Hope this helps

---

### Post by XEtedBear on 2010-12-28
Aha! Many thanks to those who created the previous 3 posts - I think my use of /sdb5 instead of /sdb may have been the cause of the problem. I mis-understood the directions in the guide I referenced, which encouraged me to find the 'Ubuntu installed partition'.

I'll try it again using the correct device name.

But I see one difficulty: my Ubuntu 'root' partition is on the second drive (sdb) - that's where /boot/grub can be found. But the MBR is on the first drive (sda). So how do I cater for that? BIOS is going to try to follow the machine code instructions in the boot sector on /sda - which I believe are, right now, corrupt and which I neeed to replace. It won't go and look on /sdb for those instructions, will it?

---

### Post by XEtedBear on 2010-12-28
Oh this is interesting: I tried the following command:
```

sudo grub-install --root-directory=/media/<UUID> /dev/sda

```

and got the message:
```

grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it. This software may cause boot or other probelms in future. Please ask its authors not to store data in the boot track

```

I had no idea who/what FlexNet is. Google tells me this company provides software licensing via an activation process. The last thing I was doing on my system before trying to reboot from Windows to Ubuntu was to install AutoCAD, which requires activation....

But, thankfully, the grub-install has fixed the problem of not being able to boot my system.

For others who may experience this problem: I was trying to install an authorised copy of  AutoCAD 2006. I was part way through the installation but abandoned it before activation was complete in order to attend to some other urgent matters. When I returned to the computer I need to reboot into Ubunut - and that when I lost about 24 hours!

---

### Post by oldfred on 2010-12-28
If you have Ubuntu on sdb and a more modern BIOS that lets you choose which drive to boot (just about BIOS with SATA support), you should install grub to sdb or whichever drive has Ubuntu and keep a windows boot loader on sda the windows drive. Then in BIOS set to boot sdb drive first. That avoids all the issues.

It is not just flexnet but a lot of windows7 software from HP & Dell as well as others. Grub is trying to work around software that violates standards, but grub/Ubuntu gets blamed.

---

### Post by XEtedBear on 2010-12-29
> **oldfred said:**
> If you have Ubuntu on sdb and a more modern BIOS that lets you choose which drive to boot (just about BIOS with SATA support), you should install grub to sdb or whichever drive has Ubuntu and keep a windows boot loader on sda the windows drive. Then in BIOS set to boot sdb drive first. That avoids all the issues.


This is a most useful suggestion - thanks. I think the BIOS on my ASUS A8V will do this (even though, REALLY annoyingly, it won't boot from a SATA attached CDROM), so I'm going to try it. However, at present I don't think I have a windows boot loader on sda  - I think I have set this back to a GRUB2 loader, which is totally vulnerable to being corrupted again when I complete the installation of AutoCAD. 

Is the Windows version of fdisk capable of writing  the necessary MBR record?

---

### Post by oldfred on 2010-12-30
I think fdisk is DOS days??

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Also you can from an Ubuntu liveCd install just the part of Lilo boot loader that goes in the MBR as it works just like windows in finding boot partition and jumping to that partition.  

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

