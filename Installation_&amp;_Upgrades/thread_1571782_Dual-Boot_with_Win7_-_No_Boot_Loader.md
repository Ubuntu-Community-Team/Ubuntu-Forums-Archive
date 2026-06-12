---
title: "Dual-Boot with Win7 - No Boot Loader"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by lotster on 2010-09-10
I have 2 separate hard drives in my PC; I have Windows 7 64-bit installed on one drive, and now I'm trying to install Ubuntu 10.04 64-bit on the other. It completed the installation successfully, no errors or anything, but when I restart I don't get an "OS Selection Menu". It just boots into Windows 7 automatically. Although I'm not entirely a Linux newbie, I don't really have any idea where to start to fix this. Can someone help me please?

---

### Post by lechien73 on 2010-09-10
It sounds like Grub may have been installed to the Master Boot Record of your second hard disk, rather than the first.

To confirm this, if you change the boot order in BIOS so that the Ubuntu disk is set to boot, does it work? Alternatively, some BIOSes now prompt you to press F10 or F12 to bring up a boot selection menu, where you can choose your second hard drive.

When you've confirmed this, we can look at either installing Grub or getting the Windows Boot Manager to load Ubuntu.

---

### Post by lotster on 2010-09-10
Wow, thank you, you were right!  I changed the boot sequence so my second hard drive boots first, and I got the Grub menu!  To a certain extent I think I prefer it this way, but since I have to learn, how would I either move Grub to my primary drive, or change my Windows loader to list Ubuntu?

---

### Post by lechien73 on 2010-09-10
There are instructions elsewhere on the forum for adding Ubuntu to the Windows Vista/7 Boot Manager, but I gave detailed instructions on my blog here:

[http://blog.mattrudge.net/2010/08/04/booting-ubuntu-through-ntldr/](http://blog.mattrudge.net/2010/08/04/booting-ubuntu-through-ntldr/)

Hope this helps :)

---

### Post by oldfred on 2010-09-10
Since you have two drives I would just leave everything alone. Change the boot order in BIOS, so your Ubuntu/grub drive boots first. Then if you every have problems you can change back and still boot windows from the windows drive.

Some Win7 software also corrupts grub2 in the MBR. So if you keep them separate you do not have to figure out what windows software is causing issues.

If you do want to install grub or windows to a MBR:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Mark Phelps on 2010-09-11
> **oldfred said:**
> Since you have two drives I would just leave everything alone. Change the boot order in BIOS, so your Ubuntu/grub drive boots first. Then if you every have problems you can change back and still boot windows from the windows drive.

+1

Or, put another way -- if it ain't broke, don't fix it!

The way you have it now is the best.  You can boot either OS on its own, and you haven't tampered with the MBR on the Win7 drive.

---

