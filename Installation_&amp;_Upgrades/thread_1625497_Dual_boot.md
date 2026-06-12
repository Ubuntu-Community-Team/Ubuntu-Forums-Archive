---
title: "Dual boot"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by no_more on 2010-11-19
Hi guys!
 
Windows advanced user here.
 
I have experience with Windows computers with pretty much no experience with any Linux. Recently I tried Ubunto running from Live USB and really much like it . My personal laptop runs Windows 7 and it is fast . However Ubunto is much much faster and I really enjoy it.
 
I want to dual-boot Ubunto 10.10 and Windows 7 . Read all the things but got a problem . I had a songle partition C (300 GB) and shinked it , left 30 GB for Ubunto. The 30 GB partition even formatted it and put a letter L.
 
Booting from the Ubunto usb I started the installaltion . I could see all the partitions but couldn't install on the 30 GB one. At the end I followed the instructions and the install went on on the main partition . I ended up with 5 partitions and only Windows 7 could boot.
 
Would you provide me with step-by-step instructions on what I should click after I start the Ubunto installation because when it comes to Linux I am really a novice. Thanks! :D

---

### Post by Hippytaff on 2010-11-19
Welcome :-)
 
If you can boot form usb, run this script and post the output here we can have a look at whats happened
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by no_more on 2010-11-19
Hi!
 
Well , I used the Windows recovery option and restored to what it was before. Currently I have one hard disk drive with only one partition C:\
 
I can shrink it and get about 30 GB from it to give Ubunto . Then I'll boot from Ubunto USB and what happens later ? How di I proceed ?

---

### Post by vinay nadig on 2010-11-19
hello there :)

i think what you need to do is when you come to the partition window, select manual option.

from there you can select what drives to use and also their formatting option.
select ext4 for the partition and then proceed.

PS : u might also want to add the swap partition during the installation.(it should be approximately twice your RAM)

good luck with the installation :)
let us know how it goes.

---

### Post by dino99 on 2010-11-19
use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by kansasnoob on 2010-11-19
You might find some of the info I posted here helpful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

I need to do a lot of work on that yet.

Before I'd make any personal partitioning recommendations I'd at the very least want to see the output of:

```
sudo fdisk -l
```

and:

```
free
```

---

### Post by jean noel on 2010-11-19
> **no_more said:**
> Hi guys!
 
Windows advanced user here.
 
I have experience with Windows computers with pretty much no experience with any Linux. Recently I tried Ubunto running from Live USB and really much like it . My personal laptop runs Windows 7 and it is fast . However Ubunto is much much faster and I really enjoy it.
 
I want to dual-boot Ubunto 10.10 and Windows 7 . Read all the things but got a problem . I had a songle partition C (300 GB) and shinked it , left 30 GB for Ubunto. The 30 GB partition even formatted it and put a letter L.
 
Booting from the Ubunto usb I started the installaltion . I could see all the partitions but couldn't install on the 30 GB one. At the end I followed the instructions and the install went on on the main partition . I ended up with 5 partitions and only Windows 7 could boot.
 
Would you provide me with step-by-step instructions on what I should click after I start the Ubunto installation because when it comes to Linux I am really a novice. Thanks! :D

May I suggest an excellent tutorial for dual booting windows and ubuntu on [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty) . Although it is about ubuntu 7.04, I find it very useful for anyone installing windows and ubuntu one the same pc.
Jean Noel

---

### Post by oldfred on 2010-11-19
While you should use windows tools with Vista or Win7 to shrink the windows partition, you cannot use them to create partitions for Ubuntu. Windows does not see nor use Linux partitions. In fact many window 7 installs use all 4 primary partitions, win uses 2 - hidden boot & system, vendor uses 2 - system recovery(drive image) & utilities. If all four are used and you create more partitions with window it converts to SFS from basic partitions which is a logical volume manager that is proprietary to windows. Per Microsoft you cannot convert back unless you totally backup, erase drive, & reinstall. (Third party tools may let you convert back).

The above is why we need to know more about your system before make specific suggestions. Post the info kansasnoob suggested.

---

