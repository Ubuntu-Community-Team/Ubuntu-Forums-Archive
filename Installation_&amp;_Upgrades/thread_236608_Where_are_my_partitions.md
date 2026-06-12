---
title: "Where are my partitions?"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by MisterD on 2006-08-15
I've just reinstalled Ubuntu after a botched 2.6.17 + NVidia drivers fiasco, and have re-partitioned everything and started from scratch. My HDD's are as follows...

1 x 100GB SATA
1 x 200GB SATA
2 x 400GB SATA

My partition layout is as follows...

/boot   100MB    /dev/sda1
swap    4GB      /dev/sda2
/       96GB     /dev/sda3
/usr    100GB    /dev/sdb1
/tmp    45GB     /dev/sdb2
/var    45GB     /dev/sdb3
/home   387GB    /dev/sdc1

I planned on mounting /dev/sdd1 as a subdirectory of my home directory once I finished the install by manually adding it to /etc/fstab. The installation finishes without a problem and I reboot. I open up /etc/fstab and notice there is no entry for /dev/sdc1 and actually no label for /home at all! Here's the output of mount...

root@thor:/# mount
/dev/sda3 on / type xfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/sda1 on /boot type ext3 (rw)
/dev/sdb2 on /tmp type xfs (rw)
/dev/sdb1 on /usr type xfs (rw)
/dev/sdb3 on /var type xfs (rw)
root@thor:/#

Where is my /home directory? So I thought I'd try mounting the partions manually somewhere else...

root@thor:/# mkdir /test1
root@thor:/# mount -t xfs -o rw /dev/sdc1 /test1
mount: /dev/sdc1 already mounted or /test1 busy
root@thor:/# mkdir /test2
root@thor:/# mount -t xfs -o rw /dev/sdd1 /test2
mount: /dev/sdd1 already mounted or /test2 busy
root@thor:/#

??? OK, already mounted, but where are they?!? I even tried checking df's output...

root@thor:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             93556984    122304  93434680   1% /
varrun                 1038232        80   1038152   1% /var/run
varlock                1038232         4   1038228   1% /var/lock
udev                   1038232       196   1038036   1% /dev
devshm                 1038232         0   1038232   0% /dev/shm
lrm                    1038232     18856   1019376   2% /lib/modules/2.6.15-23-386/volatile
/dev/sda1                97826     13682     78925  15% /boot
/dev/sdb2             45233008       548  45232460   1% /tmp
/dev/sdb1            104804996   1490988 103314008   2% /usr
/dev/sdb3             45224948    142852  45082096   1% /var
root@thor:/#

Not there either! So where is it?! Is there a size limitation or something? And if so, why did the installer let me create it in the first place?! I create a 750GB LVM spanned disk with FC5 so it can't be a Linux limit, is there an Ubuntu one? What am I missing? Any help greatly appreciated, TIA.

---

### Post by kopo88 on 2006-08-15
I can't understand everything you're trying to do, but if you made partitions and can no longer find them, it's possible that your partition table became corrupt.

When this happened to me, TestDisk ([www.cgsecurity.org/wiki/TestDisk](www.cgsecurity.org/wiki/TestDisk)) was able to repair the partition table. You can find the program on the Ultimate Boot CD ([www.ultimatebootcd.com](www.ultimatebootcd.com)) and a few Linux Live CDs.

Let me know if it helps, or if you have any questions about using it.

---

### Post by MisterD on 2006-08-15
Thanks for the link kopo88, I did in fact have corrupted partition tables, although Ubuntu and fdisk all said everything was fine, they still were holding onto their RAID0 days and thankfully TestDisk was able to delete them all and then I used fdisk to create new ones, mounted them and now everything is good, I'm back in the Terabyte Club :) Whatever disk tool the Ubuntu install uses is lame, can't even actually delete the old partitions if they're not straight, vanilla ext3 or what?! Thanks again for the link, permanently added to my toolbox :)

---

