---
title: "Removed XP hdd from double boot and now Ubuntu won't start"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by 14niki07 on 2008-07-21
Hello,

I have been running double boot Xp and Ubuntu on separate drives. Now I want to remove the XP drive to use it on another PC. When I disconnect the XP drive the system will not boot to Ubuntu. I have tried to remove the XP drive, boot from LIVE CD and restore GRUB using

```
 sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hdo)
quit
```

but this changed nothing. I spent 4 hours searching for a solution on the net but no success. Please help.

thank you

---

### Post by Potatoj316 on 2008-07-21
Are you sure you took out the correct drive?  Did your computer come with 2 HDs in it if so this is probably a BIOS change you have to make.  When starting your computer the BIOS is up for like 3 seconds press F2 (or whichever the screen says ) during that time and you will be able to do a bunch of stuff.  Look around for where it tells you about your hardware and see if it recognizes a hard drive in your computer.  If it dosent (I dont expect it to) you will have to take out the other hard drive and change the jumper (small little thing that connects a few pins and tells the hard drive if it is master, slave, or cable select) You will want to move this one to master for one drive systems (or just master) (it is probably slave now) Then  put the drive back in your computer (make sure its at the master spot on the cable) and boot it up.

---

### Post by steveneddy on 2008-07-21
Just run grub again so it will see only the one drive and correctly allow you to boot again.

Whan you remove an Operating System, Grub needs to be updated so it's not stuck looking for something that isn't there.

This may not be totally correct, but every time I remove an OS I update Grub.

---

### Post by Cresho on 2008-07-21
I think what happened was that he has a windows drive as the primary drive and ubuntu as secondary.  When he removed windows xp drive, his boot partition was removed along with it.  Ubuntu drive has no boot up at all.

I recommend you use the ubuntu drive as the primary drive next time.  If you want to reinstall, boot up from the cd install

mannual partition

you will see 2 ext3 and one swap basically 3 partitions.

usually the

1 is ext3 so format this one and use / as root
2 is swap so leave alone
3 is ext3 (partition that was originaly used as home so make sure it was ext3 and nothing else)so use /home and do not format (make sure you select ext3 and do not format or the original home partition)

use your original username and password too!

when it installs, it will format root partition and leave home alone but make sure your home is home or you will accidently fail.  all your settings and info are saved but not sure how evolution works yet in restoring that is if you use this.

---

### Post by 14niki07 on 2008-07-21
sorry, I think a little more info is needed about my system. I assembled the system my self and am pretty good at understanding bios and jumpers...My set up is Ubuntu master, XP slave. Xp was installed first then Ubuntu and Grub recognized XP with no problem, so my system was running perfectly. By looking at the portion of my GRUB/Menu.lst file I posted below you will see that GRUB is actually installed on my Linux drive. But it also installs something on the XP drive so at boot up it looks for both partitions (at least this is how I understand it). It even has a very hard time booting from LIVE CD when I disconnect the XP drive. I know I have to somehow reinstall or update GRUB, or remove the the part that points grub to my windows partition, but I have no idea how to do it. Here is my GRUB/menu.lst

*************************
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ebb9b1b3-fb43-4b5c-b76a-b0db95228b8e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ebb9b1b3-fb43-4b5c-b76a-b0db95228b8e ro single
initrd		/boot/initrd.img-2.6.24-19-generic



title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
*************************************

the mapping:

map		(hd0) (hd1)
map		(hd1) (hd0)

is specific to my configuration, and somehow I need to have grub to be looking only for hd0, but have no idea how to do it.

Please if you tell me to update or something like this be more detailed. At least point me to what you mean, and how to approach it.

Thank you all for the very prompt reply to my problem

---

### Post by confused57 on 2008-07-21
What kind of error messages are you getting when you try to boot into Ubuntu from grub?

Added:  Since you installed Ubuntu after XP, you probably have entries in fstab for the partitions on your Windows drive.  You can use the live cd to mount your root partition and comment out(place a # in front of) any fstab entries for partitions on your Windows drive.

You can determine your root partition by:
```
sudo fdisk -l
``` 
-l is a lowercase "L"

Then to mount your root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
```
replace sda1 with your root partition, then to edit fstab:
```
gksudo gedit /media/ubuntu/etc/fstab
```
just place a # in front of any Windows drive partitions mounted in fstab.  quit & save.

---

### Post by Cresho on 2008-07-21
do what the guy above says.  post error code


when I remove my xp drive, i can still boot into my ubuntu no problems.  Please post your error code.  ill be on later tonight so you wont get any replies from me but there are plenty of heads here who can help :popcorn:  can't wait to see what really caused the problem.

---

### Post by 14niki07 on 2008-07-21
it gives me

DISC BOOT ERROR, INSERT SYSTEM DISC AND PRESS ENTER

thanks

---

### Post by Potatoj316 on 2008-07-21
Does grub complain when it cant find all of its OSs.  Thats my best guess, just reinstall GRUB.

---

### Post by 14niki07 on 2008-07-21
I also suspected there is something written in the fstab but did not know how to deal with it. I will try your suggestion now.

thanks

---

### Post by 14niki07 on 2008-07-21
I tried what "confused57" suggested but there is no change. The PC would not boot again until I connect the XP drive. Now when I do 

```
fdisk -l
```

this is what I see

***************************
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000af693

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5228     2931862+  82  Linux swap / Solaris
/dev/sda3            5229       38913   270574762+   5  Extended
/dev/sda5           12645       38913   211005711    b  W95 FAT32
/dev/sda6            7661       12644    40033948+   b  W95 FAT32
/dev/sda7            5229        7659    19526944+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b179b17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 36.3 GB, 36367229952 bytes
255 heads, 63 sectors/track, 4421 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06290628

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4421    35511651    b  W95 FAT32


*****************************

my 320GB is the Linux drive and my 120GB is the XP drive. Both show as bootable. When I go to fstab I believe my XP drive is marked with an #. So I have done what you suggest and it seems in the fstab it is as it should be, but I still see both partitions as bootable, and the comp would not boot without the XP drive attached. My fstab

*******************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ebb9b1b3-fb43-4b5c-b76a-b0db95228b8e /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda7
UUID=885bdc97-4204-4244-abc5-5d78065ee936 /home           ext3    relatime        0       2
# /dev/hda5
UUID=47E5-6035  /media/hda5     vfat    utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=C182-7E37  /media/hda6     vfat    utf8,umask=007,gid=46 0       1
# /dev/hdb1
#UUID=BE04926C04922783 /media/hdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=be829f4c-532d-43a8-bb9c-33e8f2934580 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#Added by diskmounter utility
#/dev/sdb1 /media/sdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda5 /media/sda5 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda6 /media/sda6 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdc1 /media/sdc1 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdd1 /media/sdd1 vfat rw,user,fmask=0111,dmask=0000 0 0
****************

---

### Post by 14niki07 on 2008-07-21
how exactly to reinstall it?

thanks

---

### Post by upchucky on 2008-07-21
you are getting a bios error when it says to insert system disk this is before it get hard drive info from the bios.

place the drive with ubuntu in the place of the drive you took out, change its jumper to master, it should either boot, or give you grub error, if you get grub error then the bios now knows the drive is there and now you can fix the grub file and menu.lst

---

### Post by confused57 on 2008-07-21
As upchucky and Potatoj316 said, it's a bios error, but it didn't hurt to  edit your fstab.  You might want to check the hard drive boot order in bios, it may be bios is trying to boot first to the smaller hard drive sdc?

You might try booting with the live cd inserted & select to boot to first hard disk, just to see if it will boot.

---

### Post by Cresho on 2008-07-22
the way I have it, I have every single drive on my pc "cable select.  I use the sata1 and sata2 and sata3 or if it is ide, primary far end and secondary middle.

You should have all your disks cable select and on the motherboard, figure out which one is your sata0, sata1, sata2 sata0 being the first and primary drive.

You need to configure your hardware correctly to begin with.  With my rig, i can pop out winxp and pc wont complain at all.

I hope this info helps.  after configuring your hardware, of course nothing is going to work still.

---

### Post by Potatoj316 on 2008-07-22
Thankyou for noting that I called the BIOS error

---

### Post by 14niki07 on 2008-07-22
it was the HDD jumper. I had it as master main and cable select 2nd drive. When I pulled second drive and left the jumper on the first drive on master I guess bios was looking for a second drive. Now I changed it to cable select and voila...

Thank you so much for your help guys

---

### Post by Cresho on 2008-07-23
GLAD IT GOT SOLVED!  when you yank your jumper to cable select, your computer will use the cable and not the  jumper.  If you force to master and you had a second ide in master, you totally confuse the bios.

cable select is the way to go and let the cables to all the work and not the hardrive jumper.  Every single drive should use cable select unless absolutely necessery out of some wierd setup you may then need to force a master on one drive.

---

