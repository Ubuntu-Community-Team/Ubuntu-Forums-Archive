---
title: "Ubuntu Live on USB HDD"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by varunendra on 2010-04-10
Hi everybody,

Hope this is helpful for some & would provide some help to me as well.

I've a very fascinating Ubuntu Live setup with almost everything I need, but with **some minor problems as well**, for which I **need some help**.
[U][B]
Setup Details:[/B][/U]
I've installed Ubuntu 9.10 on a 320GB USB Harddisk through "create startup disk" option, & added Ubuntu Studio to it.
Initial setup is on a 4GB fat32 partition, then I've created a 26GB ext3 partition & named it "casper-rw", deleting the original "casper-rw" file located in the fat32 partition. Thus I am now able to add as many programs & other data to my setup as I wish! Rest of the harddisk consists of 3 NTFS partitions used for storage.

_**Benefits:**_
The coolest thing is that now I can boot any computer which can boot from USB, regardless of its hardware configuration, & get all my programs, settings, etc. right then & there working flawlessly as if they were installed locally.
All I've to carry is that tiny harddisk with me that contains all my data along with a capable operating system (i.e. Ubuntu Studio Live)
After booting I can do almost everything (perhaps more) that I earlier used to do on window$.
Another cool thing is that I don't have to worry about any viruses that may pre-exist on the PC I'm booting, since window$ viruses don't work on linux\\:D/

All of this combined with loads of jaw-dropping eye-candy that comes bundled with Ubuntu Studio & Compiz !!

_**Problem:**_
Now the problem.... only one of a few in this thread.
_I need to backup all my installed packages through aptoncd. But after listing them, aptoncd fails to create iso giving message that "there's not enough free space on either /tmp or the <destination folder>"_

[U]I need to increase the size of /tmp folder permanently to avoid such failures in future.
How can I do this?[/U]

Output of **df -h** is given below:
> 
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                   26G  5.3G   20G  22% /
udev                 1001M  284K 1001M   1% /dev
/dev/sdb1             4.1G  1.9G  2.3G  46% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                 1001M  384K 1001M   1% /dev/shm
tmpfs                1001M   16K 1001M   1% /tmp
none                 1001M  364K 1001M   1% /var/run
none                 1001M     0 1001M   0% /var/lock
none                 1001M     0 1001M   0% /lib/init/rw
/dev/sdb7              50G   46G  4.6G  91% /media/fag3
/dev/sdb2              26G  5.3G   20G  22% /media/casper-rw
/dev/sdb5             163G  157G  6.0G  97% /media/fag4
/dev/sdb6              56G   55G  1.4G  98% /media/fagsafeAlso, it'll be of great help if someone can direct me to some link where I can get tips for "how to get command over Frugal/Live Session setups"

-Varun

---

### Post by varunendra on 2010-04-10
Anybody home ???????
Plz hel....p..... !!![-o<

---

### Post by varunendra on 2010-04-10
Wow !
I didn't know my question was so stupid that no one even bothered to reply, let alone providing a solution !!
Anyway, I'm still waiting....... (shall try workarounds myself after complete disappointment:-\")

---

### Post by varunendra on 2010-04-12
I'm wai.........ting...!!

---

### Post by varunendra on 2010-04-14
:confused::confused::confused:

:cry:  :cry:   :cry:           :cry:           :cry:

---

