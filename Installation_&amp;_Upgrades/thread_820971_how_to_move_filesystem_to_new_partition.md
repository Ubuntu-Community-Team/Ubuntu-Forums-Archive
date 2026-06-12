---
title: "how to move filesystem to new partition"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by aaronp on 2008-06-06
Hi all,

My Ubuntu 8.04 root filesystem (Originally Ubuntu, added KDE later) is on an 11GB partition which in hindsight, should have been bigger.

I recently got rid of Windows XP all together so now have a spare 40GB partition (on a different hard drive) which I would like to move the entire root filesystem to.

Wondering if this is possible to be done safely and also if there are any step-by-step instructions available that I could follow? (in determining if I could follow them think of me as a Linux newb but fairly good at understanding concepts. e.g. I can use the command line without hassle but don't know too many commands yet!)

Thanks guys
Aaron

---

### Post by Sef on 2008-06-06
I would use [Clonezilla]("http://www.clonezilla.org/") to move it.

---

### Post by aaronp on 2008-06-11
bump

---

### Post by forger on 2008-06-11
dont have time for a step-by-step instruction, nor is it 110% safe, but it worked for me! I resized 5-6 ext3 partitions using gparted

The best way to use is either by booting up from a ubuntu livecd and head to system > administration > partition editor
*or*
you could use the live gparted that contains gnome and gparted:
[http://downloads.sourceforge.net/gparted/gparted-live-0.3.6-7.iso?modtime=1208153087&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-live-0.3.6-7.iso?modtime=1208153087&big_mirror=0)
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by Pumalite on 2008-06-11
Take your pick:
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
DAR
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

### Post by Habbit on 2008-06-11
Your best chance is possibly booting from a Live CD, mounting both the source and the destination volumes and performing the copy with tar like this:
This **example** assumes that
[LIST][*]your source is /dev/sda1
[*]your dest is /dev/sdb5, still unformatted and you want to use ext3
[*]you are using an Ubuntu Live CD:
[/LIST]
```
ubuntu@ubuntu:/$ sudo -s
/# mkdir /mnt/src /mnt/dest
/# mount -r /dev/sda1 /mnt/src
/# mkfs.ext3 /dev/sdb5
/# mount /dev/sdb5 /mnt/dest
/# cd /mnt/src
/mnt/src# tar -cp . | tar -xpv -C /mnt/dest
```
As you might guess, the copy might take long. The -p flag to tar will preserve permissions, preventing havoc when rebooting. Take note that the last C (in -xpv -C) is a capital C meaning "change directory", as opposed to the fist (in -cp) meaning "create archive". After the copy finishes, you will need to check and possibly correct the following files and programs:
[LIST]
[*]/etc/fstab, which contains the table of filesystems to be mounted. Your root partition is identified by its UUID. Run "vol_id -u" on the target device and paste the new uuid.
[*]/boot/grub/menu.lst (for GRUB 0.9x) or /boot/grub/grub.cfg (for GRUB 1.9x). Either of these files contain the bootloader config. If you are going to remove the HD with the old root partition completely you might need to reinstall GRUB (grub-install /dev/sdb in this case), but even if you're not, you need to find all the instances of the old root UUID and switch it for the new one
[/LIST]
If you are going to remove the old HD, make sure your /boot partition (if you kept it separate from the root) is copied too, then reinstall GRUB as specified above. Keep the Live CD handy for any possible problems, and good luck!

---

### Post by Irony on 2008-06-11
Do it this way; [http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

---

