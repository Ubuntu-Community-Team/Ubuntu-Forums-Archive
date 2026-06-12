---
title: "hp dv6 Dual Boot Ubuntu &amp; Windows 8 issue"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by Verister on 2013-02-09
I have the same issue. My laptop is hp dv6-6030ew. Is it possible to get those two systems to work in dual boot? If not, how can i get back to windows 8, even if i have to delete linux partitions?

---

### Post by oldfred on 2013-02-10
Welcome to the forums.

Moved to your own thread as your issues will be different.

From liveCD/DVD/Flash drive download Boot-Repair and post link.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Did you use the 64bit version of Ubuntu?
Have you turned Secure boot off?
Have you turned fast boot off?

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

Another thread with HP 
HP p6-2326 Ubuntu and windows 8 Boot DVD - see post #7 for details
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

