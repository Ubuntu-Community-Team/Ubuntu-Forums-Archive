---
title: "Install Grub on Boot Sector"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Mizled on 2007-04-25
OK This is what I'm trying to do. I have XP and VIsta installed on a SATA (500 gig HD) both work fine and the dual boot between the two works great. I've installed Ubuntu on a different IDE (120 gig) Hard Drive but I need Grub to install on the Boot Sector so I can use EasyBCD to add Grub to the Vista boot loader. So far I've been unsuccessful and I think it's due to Ubuntu installing Grub on the MBR of the separate drive. I have both the LiveCD and the Alternate CD. When using the LiveCD at the last portion of the setup I hit the Advanced Options and told it to install Grub at (hd0,1) and the install failed when I did that. I've also tried using the Alternate CD but it doesn't prompt me for the option to install Grub anywhere else...it just installs it on the MBR.

I'm getting really frustrated trying to get this setup. This thread here is what I'm trying to do [http://ubuntuforums.org/showthread.php?t=409576](http://ubuntuforums.org/showthread.php?t=409576) but like I said the Alternate CD doesn't let me choose where to install Grub. I've installed Ubuntu near 4-5 times now trying to get it to work. Any help would be appreciated. :( :confused:

---

### Post by Mizled on 2007-04-25
OK so I did the LiveCD Setup again and on the advanced options I told it to install Grub on "/dev/sda1" and that worked. I added the entry in EasyBCD and set it as (0,1) but now when I select that entry it brings up a screen that says GRUB with just a flashing cursor.  I also tried setting it as (1,1) in Easy BCD and It just gives an error saying "The selected entry could not be loaded because the application is missing or corrupt."

Suggestions? :confused:

---

### Post by Mizled on 2007-04-25
/bump

Anyone?

---

### Post by confused57 on 2007-04-25
> **Mizled said:**
> /bump

Anyone?
You could try mounting your sda1, using the live cd,  & checking the output of /boot/grub/menu.lst:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

you might need to change the root line to something like (hd1,0)?

---

### Post by Mizled on 2007-04-25
How would I change root to (1,0) ? Right now it's set as (0,0)...

Would I reinstall grub on /dev/sda1 ?

sudo grub
root (hd1,0)
setup (hd1,0) Would this worK?

---

### Post by Mizled on 2007-04-25
```
grub> find /boot/grub/stage1
   (hd0,0)
```

---

### Post by phidia on 2007-04-25
now, in grub, do > root (hd0,0) and then > setup (hd0,0)
reboot and see if it worked.

---

### Post by confused57 on 2007-04-25
> **Mizled said:**
> ```
grub> find /boot/grub/stage1
   (hd0,0)
```

Since you're using Feisty, I assume your IDE drive is recognized as sda...just to be sure, boot the live cd & check the output of:
```
sudo fdisk -l
```
the -l is a small "L"

You've probably already installed grub to the root partition by selecting to install grub to /dev/sda1, but the live cd can be used as well:
```
sudo grub
find /boot/grub/stage1
```
if this returns "root (hd0,0)", then
```
root (hd0,0)
setup (hd0,0)
quit
```
this will insure that grub is installed to the root partition

Since you're booting first to your SATA drive, grub would recognize your IDE drive as (hd1)...so you could try mounting your Ubuntu partition and try changing root to (hd1,0)...you can always change it back if it doesn't work.   I'm not sure how EasyBCD determines drives & partitions.

You could always boot first to your IDE drive and add entries to grub to boot Vista & XP.

---

### Post by Mizled on 2007-04-25
> **confused57 said:**
> 
Since you're booting first to your SATA drive, grub would recognize your IDE drive as (hd1)...so you could try mounting your Ubuntu partition and try changing root to (hd1,0)...you can always change it back if it doesn't work.   I'm not sure how EasyBCD determines drives & partitions.

How would I do this?

Do I just..

sudo grub
root (hd1,0)
quit

?

---

### Post by Mizled on 2007-04-25
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17308   139026478+   7  HPFS/NTFS
/dev/sdb2           17309       24355    56605027+   7  HPFS/NTFS
/dev/sdb3           24356       60801   292752495    7  HPFS/NTFS

```


```

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
```

```

grub> root (hd1,0)

grub> setup (hd1,0)

Error 17: Cannot mount selected partition 

```



I'm still getting the screen that says "GRUB" with the flashing cursor when I try to boot Ubuntu... :(

---

### Post by confused57 on 2007-04-25
Before you do anything else, are you able to boot your Ubuntu drive if you select it to boot first in bios, and you can boot Vista & XP by selecting your SATA drive to boot first?

You don't need to try to reinstall grub again, what I was referring to was use the method in my first reply to mount your Ubuntu partition, then edit your root in your menu.lst to (hd1,0)...then try to boot Ubuntu using EasyBCD.

When you enter:
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```
you should be able to change the line with root from (hd0,0) to (hd1,0), quit & save.

---

### Post by Mizled on 2007-04-25
Ubuntu boots up fine when selecting that drive to be the first drive in BIOS. However I really want to use the Vista Boot loader (maybe I'm making it hard on myself by doing so).

I'm booting into Ubuntu now to change root to (hd1,0)

---

### Post by Mizled on 2007-04-25
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=a6e644bb-f878-4c3d-8747-411d45100095 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=a6e644bb-f878-4c3d-8747-411d45100095 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet
```

I have not rebooted my system to save those changes but I have a feeling that will make it unbootable.. ?

---

### Post by confused57 on 2007-04-25
> **Mizled said:**
> Ubuntu boots up fine when selecting that drive to be the first drive in BIOS. However I really want to use the Vista Boot loader (maybe I'm making it hard on myself by doing so).

I'm booting into Ubuntu now to change root to (hd1,0)
Maybe I'm too late, but why don't you try adding entries to your menu.lst to boot Vista & XP?

Changing root to (hd1,0) will disable being able to boot into Ubuntu by selecting your IDE drive to boot first.

---

### Post by Mizled on 2007-04-25
I really don't want to go through two menus to boot Vista and XP...I can add them to grub but that would take me to the Vista/XP loader and then I would have to choose one of those options to boot. I want to try and keep it simplified if possible. =/

Adding Root to (hd1,0) doesn't work...It still comes up and says "GRUB" with the flashing cursor.

---

### Post by confused57 on 2007-04-25
> **Mizled said:**
> I really don't want to go through two menus to boot Vista and XP...I can add them to grub but that would take me to the Vista/XP loader and then I would have to choose one of those options to boot. I want to try and keep it simplified if possible. =/
You might want to give it a try, just to see how it works...just add entries to the very end of your meu.lst:
```
title   Windows  XP
rootnoverify  (hd1,0)
savedefault
makeactive
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader +1
```

& for Vista:
```
title   Windows Vista
rootnoverify  (hd1,1)
savedefault
makeactive
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader  +1
```

This is assuming XP is on the first partition and Vista on the 2nd.

Added:  Just saw your last post, you can use the live cd to mount your Ubuntu & change root back to (hd0,0).

---

### Post by Mizled on 2007-04-25
I will give your above suggestion a try and see how it goes. If not I may just get rid of Vista and stick to XP/Ubuntu for now. Its such a headache.

---

### Post by confused57 on 2007-04-25
> **Mizled said:**
> I will give your above suggestion a try and see how it goes. If not I may just get rid of Vista and stick to XP/Ubuntu for now. Its such a headache.
Good luck with it...I just thought you might want to try it...

---

### Post by iminj on 2007-04-25
Mizled:

I am also searching for a reliable method to dual-boot VISTA and ubuntu (in my case on the same hard drive) using easyBCD as the primary bootloader, and having GRUB placed in the ubuntu bootsector.

From time-to-time the developers at easyBCD pop into these rooms claiming this is very easy to do ... although, I have never seen detailed step-by-step instructions to achieve this objective.

**My advice:** ... visit the easyBCD forum and ask there.  Also, look at this HOWTO posted on their website:

[http://neosmart.net/wiki/display/EBCD/Linux]("http://neosmart.net/wiki/display/EBCD/Linux")

-iminj

---

### Post by Mizled on 2007-04-25
> **confused57 said:**
> You might want to give it a try, just to see how it works...just add entries to the very end of your meu.lst:
```
title   Windows  XP
rootnoverify  (hd1,0)
savedefault
makeactive
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader +1
```

& for Vista:
```
title   Windows Vista
rootnoverify  (hd1,1)
savedefault
makeactive
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader  +1
```

This is assuming XP is on the first partition and Vista on the 2nd.

Added:  Just saw your last post, you can use the live cd to mount your Ubuntu & change root back to (hd0,0).

I just get "Boot Failure" when trying the Vista one and I get a "NTDLR Missing" on the XP one...However that is how my Partitions are setup. XP first then Vista.

Also, Thanks for the suggestion iminj I will try that.

---

