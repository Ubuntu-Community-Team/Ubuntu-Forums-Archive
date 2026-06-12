---
title: "Partition issue"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by xigen on 2009-12-02
I recently installed 9.04  - however, It looks like I got a little bit stingy with the amount of space I allocated to the OS.

I then added a couple of gigs to /dev/sda7  .. and thought everything would be fine.

Unfortunately, when I look at the disk useage analyzer it shows me that /wilson is full.   ... Rut.Ro.

How do I increase the size of /wilson?
or
would it be better to point /wilson at my previous /home/wilson

Ubuntu 9.04
Ubuntu 9.10 (on a different partition)
very large /home/wilson area
32bit
500 gig of disk space.


wilson@wilson-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             5.3G  3.9G  1.1G  79% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  112K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  156K 1007M   1% /dev
tmpfs                1007M   49M  958M   5% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-16-generic/volatile
/dev/sda6             440G  211G  208G  51% /media/disk

---

### Post by raymondh on 2009-12-02
> **xigen said:**
> I recently installed 9.04  - however, It looks like I got a little bit stingy with the amount of space I allocated to the OS.

I then added a couple of gigs to /dev/sda7  .. and thought everything would be fine.

Unfortunately, when I look at the disk useage analyzer it shows me that /wilson is full.   ... Rut.Ro.

How do I increase the size of /wilson?
or
would it be better to point /wilson at my previous /home/wilson

Ubuntu 9.04
Ubuntu 9.10 (on a different partition)
very large /home/wilson area
32bit
500 gig of disk space.


wilson@wilson-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             5.3G  3.9G  1.1G  79% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  112K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  156K 1007M   1% /dev
tmpfs                1007M   49M  958M   5% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-16-generic/volatile
/dev/sda6             440G  211G  208G  51% /media/disk

Kindly .... access gparted (system > administration > partition editor).  It'll give you a window of your HD.  If you have the keyboard, press PrtScrn and save to desktop.  If no keyboard, access "take a screenshot" (applications > accessories).

Paste/attach the screenshot in your next post.  It'll help us visualize the whole HD.

Thanks,

---

### Post by xigen on 2009-12-03
A screenshot w/ Gpartd ... as requested.

Cheers.

---

### Post by raymondh on 2009-12-03
> **xigen said:**
> A screenshot w/ Gpartd ... as requested.

Cheers.

Thanks.  Make sure you have working/tested back-ups of your files.

1.  Have you [cleared out trash]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

2.  Boot into a liveCD (or liveUSB) and go live session (TRY UBUNTU....) which will unmount partitions.  To double check, right click on any partition is if given the option to unmount, do so.  For swap, select swapoff.

-  Click to highlight sda6.  Select resize.  Grab the RIGHT arrow and drag LEFT to shrink appropriately (say giving 10GB).  You can monitor size changes as you do so.  Review and APPLY

-  Click to highlight sda7.  Select Resize/move.  You can either Move the whole partition to the left to occupy the recently freed-up space and then resize by grabbing the right and extending to the right..... Or, outright resize by GRABBING the left and moving LEFT to occupy the unallocated space. 

*  I prefer to move then enlarge to the right.  Just my .02

Regards,

---

