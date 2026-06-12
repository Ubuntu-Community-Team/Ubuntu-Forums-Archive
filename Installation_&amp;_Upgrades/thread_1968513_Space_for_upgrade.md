---
title: "Space for upgrade"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by asus701user on 2012-04-29
I am trying to upgrade to 11.04 from 10.04 but when I run Update I am told there is not enough disc space.

Because I have limited disc space (on Asus eeepc) I have previously moved /home to a SD card. The disc configuration is:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              3620376   2302920   1133548  68% /
none                     1020580       252       1020328   1% /dev
none                     1026200       168      1026032   1% /dev/shm
none                     1026200       644   1025556      1% /var/run
none                     1026200         0   1026200       0% /var/lock
/dev/sdb1              3913244    990508   2723952  27% /home
```I have removed everything I can but there is still not enough space on sda1.

I would rather not do a complete reinstall, because repartitioning and moving directories to sd is complicated, and I would like to keep any local settings like fstab.

How can I get the Update manager to use sdb1 for any installation files etc?

Alternatively can I move anything else (like var or dev or etc) to sdb1?

Many thanks

---

### Post by GnuSense on 2012-04-29
First thing you should do is clean out all the old programs from /var/cache.

sudo apt-get clean

That probably won't give you enough room, though.  The big space hog in the upgrade process is the /var/cache directory, specifically /var/cache/apt/archives. What I would consider doing is making moving that directory to another machine that you are networked to, then making link from that machine to /var/cache/apt/archives.

Unfortunately I don't have time to explain exactly how to do that (I'd mount a samba share in my /etc/fstab so it is there at boot). Once you've successfully upgraded your can clean out your archive again with 'apt-get clean' and move the reduced directory back to your netbook.

---

### Post by asus701user on 2012-05-01
Thanks for that. I have already run clean and autoclean. I have installed Partition Editor but it seems it won't resize the partition on sdb1 where /home is located while /home is in use. Since home is needed to run the system I am stuck. I tried to unmount the drive in order to resize it and now (despite not having changed fstab) the machine won't boot at all and doesn't seem to be fnding the ssd drive.

So I'll give up this upgrade and see if it is worth trying a clean instal.

---

