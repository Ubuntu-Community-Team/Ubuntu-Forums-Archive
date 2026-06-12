---
title: "Upgraded to Edgy...Wheres drive?"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by computergirl on 2007-09-23
Hi 
Im still new to this Ubuntu "stuff" have a question
I upgraded to Edgy Eft 6.10. from 6.06. 
I have a dual boot (windows ubuntu) machine. Before I was able to "see" my hard drive (Presario) and look at the files and run some on it with wine. Then I upgraded
Now when I go into the places->computer->  all I see is the "filesystem" from Ubuntu.
Where did my HDD presario go?
 Can I get it to show again?? How can I do this?
Thank you-

---

### Post by banewman on 2007-09-23
I assume it is your windows partition that you want available. If so in terminal type - sudo gconf-editor - give your password - click on apps - scroll to nautilus and click - click on desktop and see if " volumes visible " is checked. Most times that will show the other partitions that are in /etc/fstab. :)

---

### Post by computergirl on 2007-09-23
"I assume it is your windows partition that you want available. If so in terminal type - sudo gconf-editor - give your password - click on apps - scroll to nautilus and click - click on desktop and see if " volumes visible " is checked. Most times that will show the other partitions that are in /etc/fstab."

 Yes, its my windows partition. I tried what you explained, but the partition still does not show after completing your steps.

---

### Post by logos34 on 2007-09-23
Does it show up in fdisk?

**sudo fdisk -l **(lowercase L)

Post your fstab too:

**cat /etc/fstab**

---

### Post by computergirl on 2007-09-23
Disk /dev/hda: 120.0 GB, 120060444672 bytes
240 heads, 63 sectors/track, 15508 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         566     4278928+   b  W95 FAT32
/dev/hda2   *         567        4079    26558280    7  HPFS/NTFS
/dev/hda3            4080        7240    23897160    f  W95 Ext'd (LBA)
/dev/hda4            7241       15367    61440120   83  Linux
/dev/hda5            7064        7240     1338088+  82  Linux swap / Solaris
/dev/hda6   *        4080        6937    21606417   83  Linux
/dev/hda7            6938        7063      952528+  82  Linux swap / Solaris

Partition table entries are not in disk order
root@user-desktop:~# 
.

sorry for not knowing how to get to this:
cat /etc/fstab

Im not that good with linux/unix...Ive been trying to get off Windows to learn this new system. Im a student thats learning programming langos and web site script, Most of my time is on windows ( ;-( but  I REAlly want to learn all this - 
Thank you for helping me out.[http://ubuntuforums.org/images/smilies/icon_wink.gif](http://ubuntuforums.org/images/smilies/icon_wink.gif)

---

### Post by logos34 on 2007-09-23
enter cat /etc/fstab in terminal

---

### Post by logos34 on 2007-09-23
You need only one swap partition, so get rid of the other.

Also, you need to take out the boot symbol (*) on hda6.

**gksudo gparted**

right-click on hda6>manage flags>untick 'boot' box

---

### Post by computergirl on 2007-09-23
Hows this?? Doh! is me!

root@user-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=85bbc39a-90fc-44ab-88b5-28e41bc27ab1 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda7 -- converted during upgrade to edgy
UUID=66b6de97-b3af-4284-bd48-d7e94959f068 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
root@user-desktop:~# 


Whats UUID????? Is it like a windows reg key?

---

### Post by computergirl on 2007-09-23
Partition table entries are not in disk order
root@user-desktop:~# gksudo gparted
root@user-desktop:~# 



Its not in order.. When I run qpart from the desktop it also stated theres no drive info.

---

### Post by computergirl on 2007-09-23
Can I remove the partition boot it from windows...?

---

### Post by logos34 on 2007-09-23
> Whats UUID????? Is it like a windows reg key?

The [wiki ]("http://en.wikipedia.org/wiki/UUID")explains it better than I can.

Ubuntu started using them with edgy.  You don't really need them for a single disk setup like yours.  IMO they are a pain in the a**

Try this with fstab:
[B]
sudo cp /etc/fstab /etc/fstab_backup

gksudo gedit /etc/fstab[/B]

add these lines:

> /dev/hda1 /media/hda1 vfat defaults,umask=0000 0 0
/dev/hda2 /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 0

create the mount points if they don't already exist:

**ls /media**

If no hda1 and 2, make them:
[B]
sudo mkdir /media/hda1
sudo mkdir /media/hda2[/B]

mount them:
[B]
sudo mount -a[/B]

Get ntfs-3g driver for write support to ntfs windows partition:
[B]
sudo apt-get install ntfs-config

gksudo ntfs-config[/B]

>enable write support internal drive

---

### Post by logos34 on 2007-09-23
> **computergirl said:**
> Partition table entries are not in disk order
root@user-desktop:~# gksudo gparted
root@user-desktop:~# 

Its not in order.. When I run qpart from the desktop it also stated theres no drive info.

Don't worry about the 'not in disk order' thing...fdisk lists them in order, but that's not necessarily how they actually are on the disk.  

SO gparted opens and it doesn't detect the drive/no drive info?

---

### Post by computergirl on 2007-09-23
Friend..where did you go?? ;-)

---

### Post by computergirl on 2007-09-23
So sorry... I didnt see I had 2 pages. Anyhooo.. I got POed at the system, deleted the 4 partitions...reinstalled 6.06 got my HDD fro the presario back! Im printing your information out incase Im daring .....to upgrade and have problems like this again. 
Plus, the stupid wine doesnt work with Adobe Flash CS3...now im REALLY mad...Going to throw the tower out the window!

Thank you for all your help....

---

