---
title: "Hard disk not detecting. Please help.."
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by bujji_gadu on 2008-06-14
Hi, I am trying to install the ubuntu 64bi on the following.. but it does not detect hard disk at all.. Please help

CD check came out fine. Everything seems to be fine. I can boot using the CD. But no hard disk is being detected. Windows XP is fine.. partitioned the hard sik to 2- 320gb's?? one partition has winxp. The other is also formatted to NTFS... 

PLEASE HELP

E6850
Abit Ip35 Pro
WD6400AAKS
3gb RAM
Evga 8800gs

---

### Post by PmDematagoda on 2008-06-14
How is your hard drive set-up? Is it SATA?

---

### Post by bujji_gadu on 2008-06-14
yes it is SATA

---

### Post by bobbob1016 on 2008-06-14
Are you trying to install Ubuntu on the second NTFS partition, or just get data recognized?  If you want to install Ubuntu, you should leave the second partition unformatted, Ubuntu can format the partition itself.  If you want the data recognized, try searching the forums for "add ntfs drive" or "new hard drive".
RUN THESE COMMANDS WITHOUT QUOTES
After a quick search I found that you should type the command
"sudo mount -t ntfs-3g -o force [device] [mount path]"
First open a terminal (Applications -> Accessories -> Terminal) and type:
"sudo mkdir /media/XP" or whatever you want to call the partition, you need /media/ but you can put whatever you want after it.

To find the device, as in the partition:
Click System -> Administration -> Partition Editor

It should show you all your partitions, find the drive with the ntfs partition, hda is your first physical drive, could be sda if it is sata.  hda1 or sda1 would be the first partition of said drive.
So you'd want to do "sudo mount -t ntfs-3g /dev/hda2 /media/XP" if your partition is hda2, and the directory you made before was /media/XP.  You should now see it on the desktop.

This is not a permanent fix, it will be gone after a reboot.  If this loads your data fine, in a terminal type "sudo cp /etc/fstab /etc/fstab-backup" then "sudo gedit /etc/fstab" and add the line:
"[device] /media/XP    ntfs    defaults,umask=007,gid=46 0       1" where [device] is /dev/sda1 or hda1 or whichever you determined before and save the file.  Reboot, and the partition should show up on your desktop.

---

### Post by bujji_gadu on 2008-06-14
I want to install ubuntu on the second partition. Firs tpartition is for XP. That is why firs I did not format the second partition. But it does not detect the hard drive at all. So I went ahead and formatted the second partition to see it will detect. but it did not.

I checked - system> Administration> partition editior.... it does not detect hard drive .... 

Do i need to issue these commands??

---

### Post by bobbob1016 on 2008-06-14
Is the SATA drive on the motherboard, or on an add on card?  It should show up normally if it is on the motherboard.  Beyond that, I'm not sure.

---

