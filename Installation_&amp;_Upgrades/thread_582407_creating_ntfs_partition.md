---
title: "creating ntfs partition"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Kevin Jones on 2007-10-19
Helle everyone,

I recently upgraded to ubuntu from windows. During the download of the ubuntu OS I lost the windows operating system.
Dell gave me a cd of windows vista operating system but I am unable to load it because there is no NTFS partition to install it to. Is it possible to create an NTFS partition either from the grub or from Ubuntu terminal.

Thanks 

Kevin Jones

---

### Post by scrooge_74 on 2007-10-19
Use the Live CD and use [Gparted ]("http://gparted.sourceforge.net/")to create a partition, it could also be that the partition is there, but you somehow manage to not include it in GRUB

open a terminal and type df, and check the partitions that show up.  Then you could edit GRUB so it can  include it.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Boot_Menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Boot_Menu)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28reinstall%29%7C%28grub%29](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28reinstall%29%7C%28grub%29)

---

### Post by Kevin Jones on 2007-10-19
This is the result of the df, which I typed into the terminal

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            234330488   3254956 219172172   2% /
varrun                 1037212       104   1037108   1% /var/run
varlock                1037212         0   1037212   0% /var/lock
procbususb             1037212       124   1037088   1% /proc/bus/usb
udev                   1037212       124   1037088   1% /dev
devshm                 1037212         0   1037212   0% /dev/shm
lrm                    1037212     33788   1003424   4% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1               125668    105710     19958  85% /media/UDISK 2.0
kevin@kevin-desktop:~$ 


I am unable to tell if windows is still here, or if it is hidden, or if I shall have to download it again.Thanks for the help scrooge, I am going to follow the links you suggested
kevin

---

### Post by scrooge_74 on 2007-10-19
It looks like you only have one partition plus a usb disk on the machine at this moment.

I am guessing that at install time you did not do a manual install so the Install script just wiped clean your disk.

My advice to you before going further, backup your data.  Then use your Windows cd to reinstall the system to its original state, then use the Live CD as to install Ubuntu again.

What you should do is make three partitions for Ubuntu: one for your system files (about 2 GB at least) and another for your /home folder (so if in future you want to change Linux distro or you get into trouble your data is save and sound away from the system files) and your swap partition.

Here is a good link on [how to]("http://www.psychocats.net/ubuntu/installing") do it, plus some other usefull info. 

It sounds like a lot of info, but it will help in the long run.

Good luck and keep posting any doubts

EDIT: when you finish you should have 4 partitions in the disk: XP, Ubuntu system, /home, and swap

---

