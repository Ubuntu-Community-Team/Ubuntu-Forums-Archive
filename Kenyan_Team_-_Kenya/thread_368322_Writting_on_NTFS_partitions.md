---
title: "Writting on NTFS partitions"
date: 2007-02-23
forum: Kenyan Team - Kenya
---

### Post by mwero001 on 2007-02-23
Semeni? Am kinda new in this but I was wondering if anyone knows how mount ntfs partions in write mode in ubuntu.Mounting and reading is'nt much of a problem coz I configured them to be mounted during boot time. Peace.

---

### Post by mizar001 on 2007-02-23
For what i know, writing on a ntfs partition from linux is not a certified procedure. It's not a recommended action, even if a write utility exists.

You can convert the ntfs partitions in a fat32 format, and this is the recommended way to read/write from windows based partitions. 

Another method if you have a local network is to start windows and share disks on net, and from another machine hosting ubuntu, mount these partitions with samba.

---

### Post by Jussi Kukkonen on 2007-02-23
The wiki is your friend:
[https://help.ubuntu.com/community/MountingWindowsPartitions#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by njukey on 2007-04-05
ntfs-3g will allow you to read and write your NTFS partitions, just use aptitude to install it
i.e
sudo apt-get install ntfs-3g

after that you edit the file /etc/fstab to to be as follows 

/dev/hda1 /mnt/windows ntfs-3g -o silent,umask=0,locale=utf8

i think it should work just remember to replace hda1 with yor device name and also mnt/windows with the mount directory

---

### Post by njukey on 2007-04-05
ntfs-3g will allow you to read and write your NTFS partitions, just use apt to install it
i.e

$ sudo apt-get install ntfs-3g

after that you edit the file /etc/fstab to to be as follows 

/dev/hda1 /mnt/windows ntfs-3g -o silent,umask=0,locale=utf8

i think it should work, just remember to replace hda1 with your device name and also mnt/windows with the mount directory

---

### Post by garybrlow on 2007-04-05
Read information at [www.ntfs-3g.org](www.ntfs-3g.org). Use ntfs-3g-config to install and set everything in just 2 clicks.


Cheers!!!


GaryBrlow :biggrin:

---

### Post by Gargamella on 2007-05-15
Thank you very much I didn't know it... ;D

now  I am very happier

Have a nice day

---

