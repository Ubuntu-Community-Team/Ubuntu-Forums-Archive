---
title: "Repair boot after windows install"
date: 2015-04-22
forum: Installation &amp; Upgrades
---

### Post by dyoung287 on 2015-04-22
Hi I have an old windows 7 laptop that I installed ubuntu and dual booted with windows which I upgraded to windows 8 tech preview. Grub worked fine with both for a few weeks. Windows 10 has now upgraded  to a new build and broken my boot and I get grub recovery instead. 

I have booted a ubuntu live cd and ran boot repair with default settings. 

It restored an mbr and now when I boot I get the message windows failed to start because a required device is inaccessible. 

I was told to paste the boot repair url here.
paste.ubuntu.com/10868109

---

### Post by oldfred on 2015-04-22
Windows did its usuallly delete of the Linux partition in the extended partition.

Use testdisk and find the partition that should be in the unallocated space. Then restore the grub boot loader.

If you cannot boot Windows now with  a Windows boot loader you need to repair Windows first. Grub only boots working Windows. And Windows 8 or later must have the fast startup or always on hibernation turned off if dual booting. Even dual booting several versions of Windows.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

You can use boot repair to restore grub boot loader once partition is restored & Windows is fixed.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Mark Phelps on 2015-04-23
It's not a good idea to be running the Win10 Tech Preview on a drive you share with an OS you rely on for day-to-day use.  I used to do that and got tired of Win10 trashing the other OS on nearly a daily basis.  So, I moved Win10 to its own drive, and now, I don't have to repair the other OSs.

Also, in addition to disabling FastStartup in Win10, if you want to be able to mount and read the NTFS partitions while in Ubuntu, then be sure to use ShutDown from Win10, not Restart.  That's because Restart ignores the FastStartup being disabled and forces the machine into hibernation anyway.

---

