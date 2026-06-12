---
title: "how to safely uninstall another Ubuntu on dual boot"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by orduek on 2010-01-26
Hi,
For testing posposes I installed another mythbuntu (9.10) in dual boot next to my older (9.04) one. 
I now want to uninstall it but ofcourse the grub is now loaded from there, so I can't just delete the partition.
How can I safely remove it and come back to my old grub?

---

### Post by oldfred on 2010-01-26
If you can boot into your older ubuntu you do not need to chroot. Where X,Y is drive-X, partition-Y if known or use sudo fdisk -l to see partitions. Note grub numbering is different than Ubuntu or new grub.
old grub sda1=(hd0,0), partition numbering in old grub starts at 0.

If you need to chroot:

sudo mount /dev/sdXY/mnt
for i in dev proc sys; do mount --bind /$i /mnt/$i; done
sudo chroot  /mnt

From working install this is all that is required to reinstall grub or after chroot above:

grub
at grub prompt:
find /boot/grub/stage1 #you will get a response such as root (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition
setup (hd0)  # if it is drive0 or sda
quit

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

