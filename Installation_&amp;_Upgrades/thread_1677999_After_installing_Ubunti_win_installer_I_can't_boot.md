---
title: "After installing Ubunti win installer I can't boot up my laptop"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by EmZata on 2011-01-29
Hello. I made the BIG mistake to install Ubuntu. I have Windows 7 installed on my laptop. I wanted to try Ubuntu so I downloaded the win installer. My win 7 is on partition C: and I installed Ubuntu on D:. I ran Ubuntu and everything was okey. It promted that there are updates avalible. It started downloading them but I was on a free internet and it succeded to download part of them aroudn 100mb. Through he instalation of the updates it promted for some grub settings. I choosed a device - my Hard disk and that's all. Then I turned off the laptop and after swtitching it on it shows this: 

error: No such device : 0e8393a9-5efe-41fd-bbbe-19d4e3e9f46e
grub rescue:

Please tell me how to fix this. I want my Windows 7 back and I won't touch linux again..

---

### Post by oldfred on 2011-01-29
If you installed wubi, it has a bug that installs grub to the MBR when you should still have the windows boot loader in the MBR.

Restore MBR for win7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by EmZata on 2011-01-29
Thanks a lot for the info. It's fixed now. Wow I was so angry.. But if there is such a major bug why isn't it stated in the ubuntu site ?

---

### Post by oldfred on 2011-01-29
Not sure. It has been posted as a bug, but different groups seem to be passing the buck. Wubi is not the full blown Ubuntu on separate partitions, but a system that looks and works like Ubuntu but uses windows to boot and is just a file inside the windows partition. 

Some then do not support it as well as the full system, but it is there just for users like you to test Ubuntu without having to create partitions and make changes to their system. You can uninstall like any other windows program.

Even here on the forums only a few users know much about wubi, including me as I have never installed it.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

Even the developer of wubi recognizes that you will not stay with wubi long term.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

And yes it did not work as advertised for you. It should work ok now, just follow the threads on wubi issues incase of problems.

---

