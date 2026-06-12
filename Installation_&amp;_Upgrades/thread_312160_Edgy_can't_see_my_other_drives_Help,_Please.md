---
title: "Edgy can't see my other drives? Help, Please"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by mdk1967 on 2006-12-04
Had a HDD failure (the dreaded "Tink, Tink, Tink" sound of a hard drive crash) so I decided to install E#dgy.

System is set up as follows:
100GB WD PATA Drive - Used for the Edgy Install
250GB WD PATA Drive - Music
500GB Seagate PATA Drive - Movies

Installation saw them as:

100GB HDA1
250GB HDB1
500GB HDC1

I chose to use the entire drive (on the 100GB)

The install went fine, with "seemingly" no errors. 

I can:

sudo fdisk /dev/hdb1 and see the 250GB drive partition info
sudo fdisk /dev/hdc1 and see the 500GB drive partition info
sudo hdparm -T /dev/hdb1 and get results
sudo hdparm -T /dev/hdb1 and get results

I created mount points for them in /media
I edited /etc/fstab and added them

I remounted /etc/fstab with:

sudo mount -a

I cannot see the data on them.

I know I'm missing something simple, but it escapes me at the moment so I'd appreciate some assistance.

---

### Post by mdk1967 on 2006-12-04
Seems to be working now, but the first 10 times I tried to access my other 2 drives, they showed up as being blank, with no data on them. then the data magically appeared out of nowhere the last time I tried to access the drive...hmm

time for a reboot and see if they mount

---

### Post by PurplePenguin on 2006-12-04
Hmmm... you rebooted 44 minutes ago and no word yet? :)  I hope it's working for you!

---

### Post by mdk1967 on 2006-12-04
Yeah it's working...

I'm stumped as to why it wouldnt see anything before...

---

