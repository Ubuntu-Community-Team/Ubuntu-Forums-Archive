---
title: "Install Wizard detects wrong windows 7 partition - Xubuntu 14.0"
date: 2015-07-27
forum: Installation &amp; Upgrades
---

### Post by manue-l on 2015-07-27
Hi

I'm trying to install Xubuntu alongside Windows, in my Dell Inspiron 1750. Windows 7 is  installed already , and I have a partition that stores the backup image of windows (factory). When I choose to install Xubuntu alongside Windows, the system tries to install everything on the backup partition (there is no UEFI stuff).

If I choose a custom installation, then there is the following description:

dev/sda:
    dev/sda1 (Windows 7 Loader)
    dev/sda2 'unknown'


Accordingly to its sizes, dev/sda1 is the windows backup and dev/sda2 is where windows 7 is installed. If I select "Install alongside windows 7", the system tries to install Xubuntu in dev/sda1.

Is it possible to fix this issue? Should I do all manually? 

Thanks.
Manuel.

---

### Post by yancek on 2015-07-27
> Should I do all manually?

Yes.  You will have some control that way as the "Alongside" option is pretty much an auto-install and you have to just hope for the best.  First thing I would check, you have two partitions, correct?  Do they take up the entire drive?  If so, you can't install until you change that.    You can boot Xubuntu install medium and open a terminal, then type the following command to get info and post here:  sudo fdisk -l(Lower Case Letter L in the command).  If you know your windows partitions are taking up the entire drive, go to Disk Management in windows and shrink one of the partitions to create space for Xubuntu.  You might need to run a filesystem check after doing this and reboot.  I don't use windows so I'm not really sure what process would be needed but I would guess based on the info you posted that you don't have any free space on the system.

---

