---
title: "Adding new partition for Ubuntu"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by minstn on 2008-05-31
Hi group! On my PC i have 1 disk with 2 partitions, one is holding WinXP and the other is for Ubuntu Hardy. now i want to remove winxp completely and make the windows partition part of Ubuntu root. What is the easiest way to do that?

P.S. anybody knows of a nice Disk Manager for Ubuntu (similar to WinXP)

thanks in advance!

---

### Post by housam on 2008-05-31
Use Gparted ( on ubuntu live cd ) to format the windows partition to ext3 , then add it to the root partition

---

### Post by minstn on 2008-05-31
thanks i will try Gparted! both of my partitions are actually NTFS..

---

### Post by housam on 2008-05-31
> **minstn said:**
> thanks i will try Gparted! both of my partitions are actually NTFS..

Ubuntu can not be installed on a ntfs format partition. it must be ext3 format.

---

### Post by minstn on 2008-05-31
yes you are right, here is the output of df:

```

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
              ext3    13563852   7965312   4914948  62% /
varrun       tmpfs     1557768       128   1557640   1% /var/run
varlock      tmpfs     1557768         0   1557768   0% /var/lock
udev         tmpfs     1557768        68   1557700   1% /dev
devshm       tmpfs     1557768        12   1557756   1% /dev/shm
/dev/scd0      udf     7359424   7359424         0 100% /media/cdrom0
/dev/sdc1     vfat   976521536 369838944 606682592  38% /media/My Book
/dev/sdd1     vfat   117189600  48694048  68495552  42% /media/LOCAL DISK

```

i just realized that i could just extend my /host/ubuntu/disks/root.disk as it sits on 149GB disk, but i'm not sure how can i do that. i installed Ubuntu Hardy by running setup utility on the Live CD from WinXP. any ideas?

thanks a lot!

---

### Post by logos34 on 2008-05-31
> **minstn said:**
> yes you are right, here is the output of df:

```

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
              ext3    13563852   7965312   4914948  62% /
```


...i installed Ubuntu Hardy by running setup utility on the Live CD from WinXP. any ideas?

Sound and looks like you did a Wubi install.  In which case you'll need to use[ LVPM ]("http://lubi.sourceforge.net/lvpm.html")to convert it.

Post your 

sudo fdisk -l

---

### Post by housam on 2008-05-31
If you have Hardy live cd , boot from it and go for applications >> accessories >> terminal , and type in the terminal:
```
sudo fdisk -l
```
where -l is a small L and post the results

Also go for system >> admin. >> partition editor and take a screen shot of the image and post it too.( for the screen shot : go for applications >> accessories >> take a screenshot )

---

