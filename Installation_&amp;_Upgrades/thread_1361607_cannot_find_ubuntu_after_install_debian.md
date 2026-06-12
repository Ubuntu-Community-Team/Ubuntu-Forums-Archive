---
title: "cannot find ubuntu after install debian"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by black&amp;blue on 2009-12-22
at begining,my computer has two OS,XP and ubuntu9.10,then i install debian as the third OS.
After debian installed success,i can't find ubuntu in grub when boot up,only xp and debian can choose.it seems ubuntu still in harddisk.
partitions of my laptop
```
 
sda1 xp                  primary
sda5 ubuntu            logical
sda6 swap               logical
sda7 nofilesystem    logical
sda8 debian             logical
sda9 swap               logical

```
what can i do to solve the problem
i tried to boot with a ubuntu liveCD,and input 'sudo grub'in terminal,respond with 'no command found'.

---

### Post by lemming465 on 2009-12-24
Hmmm.  Evidently the Debian grub install process is less aggressive than Ubuntu about identifying other operating systems sharing the disk.  The simplest solution is probably to back to Ubuntu booting.  You don't show signs of a separate boot partition, so I'm assuming /boot is a directory on /, not a mount point.  So what you want to do is boot the Ubuntu live desktop CD, open a terminal prompt, and do a boot repair like this```
sudo -i
mkdir /media/sda5
mount /dev/sda5 /mount/sda5
cd /mount/sda5
for f in sys dev proc; do mount -o bind /$f $f; done
chroot .
grub-install
```

---

