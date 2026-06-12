---
title: "Too many partitions after 2 failed installs"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by nabbster on 2009-12-27
Hi,

I have installed ubuntu 9.04 but the first 2 attempts failed due to a glitch with the partition size slider basically i ended up with 2 partitions to small for the updates after the install.

I googled and fixed this but I have been left with a lot of unused space. I downloaded gpart and as I am new to linux I have no idea what partitons I can format/merge.

To top it off its on a laptop with vista and a hidden vista restore partition that 'I DO NOT WANT TO MESS UP'

Can some one be kind enough to tell me how to check what to look for to determin what partitons i can delete?

I have enclosed an image of gpart

Thanks

---

### Post by apmcd47 on 2009-12-27
Post the output of ```
df
```so that we can determine which partitions are in use. I take it you have a gparted live CD to do the actual repartitioning work?

Andrew

---

### Post by nabbster on 2009-12-27
Hi no i wasn't using livecd but i will be now

here is output.

bobb@bobb-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda9             93950916  10099100  79079312  12% /
tmpfs                  1863624         0   1863624   0% /lib/init/rw
varrun                 1863624       224   1863400   1% /var/run
varlock                1863624         0   1863624   0% /var/lock
udev                   1863624       180   1863444   1% /dev
tmpfs                  1863624      1036   1862588   1% /dev/shm
lrm                    1863624      2560   1861064   1% /lib/modules/2.6.28-17-generic/volatile
/dev/sda7              2403388   2339720         0 100% /media/disk
/dev/sda5             98844908   1216432  92607364   2% /media/disk-1
bobb@bobb-laptop:~$

---

### Post by Bartender on 2009-12-27
I'd download and burn to disc a copy of the latest stable version of GPartedLiveCD (GPLCD) link under my sig.

Download the latest version, burn the .iso to a CD like you would an Ubuntu install download, then boot from the CD.  Delete all the partitions inside the extended.  If you wanted to you could even delete the extended and re-create it using all the space instead of leaving that 1GB hanging out there useless.

From there it's up to you.  Simplest would be to create one big ext3 or 4 logical partition inside the extended, then install Ubuntu to that.  Or you could manually set up logical partitions for /, swap, and /home, then when you boot from Ubuntu install CD you'd go into manual partition and mount each partition accordingly.  That's easy to do once you've done it but confusing the first time.

---

### Post by oldfred on 2009-12-27
The gparted you show has locks (key symbol) so are you running it from inside your install. You cannot edit partitions while mounted or you cannot edit anything with the key symbol. 

The df did not show which swap is used but if you are running the gparted from within ubuntu then it is sda10 which would make sense since you last install is one sda9.

Unless you want to reuse for data sda5,6,7 & 8 you can delete them all. It is best to use gparted from a liveCD to edit partitions but if you are not using them you could unmount them (key says they are mounted) and then you should be able to delete them.

---

### Post by nabbster on 2009-12-28
Thanks apart from grub messing around that went well

---

