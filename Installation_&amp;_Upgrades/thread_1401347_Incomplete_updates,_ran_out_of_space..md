---
title: "Incomplete updates, ran out of space."
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by laurabray on 2010-02-08
I only installed Ubuntu with 8GB because this is my first time and I've just been exploring (I didn't know any better but now I do!).  But I kept installing the recommended updates/packages and finally one day in the middle of downloading/installing these updates/packages, I ran out of space.  The next time I tried to boot Ubuntu, I got a strange log-in screen and a little error message in the upper right-hand corner of the screen saying something about invalid something or other and I needed to reboot.

So here I am running a LiveCD trying to figure out if there's any way I can update my system without doing a full re-install.  I've also got Vista on my machine.  If I try to install packages on my LiveCD, can I fix it?  I need help!  Also, if this isn't possible, are all my Ubuntu files lost forever? :(

---

### Post by kansasnoob on 2010-02-08
From the Live Desktop go to terminal and run:

```
sudo fdisk -l
```

BTW that's a lower case L, post the results here.

---

### Post by Letian on 2010-02-08
try apt-get clean on the terminal
this should empty the apt cache and free up some space for you.
ubuntu normally keeps downloaded packages in a cache so this command will clear up some space

hope u succeed

---

### Post by Letian on 2010-02-08
oh forgot to mention if your home directory is full you normally wont be able to log in graphically....

ctrl+alt+f2 should take u to command line log in 
so there u can log in and do as i prescribed above...

---

### Post by laurabray on 2010-02-08
```
Disk /dev/sda: 250.1 GB
4 heads, 44 sectors/track
Units = Cylinders of 176 * 512 = 90112 bytes
Disk identifier ox97646c29

Device Boot   Start        End             id      System
/dev/sda1      1       127973    11261533+    1c    Hidden W95 FAT32 (LBA)
/dev/sda2     127973  1515405  122094000    7      HPFS/NTFS
/dev/sda3    1515406 2774983  110842864    f       W95 Ext'd (LBA)
/dev/sda5    1515406 2774983  110842842    7     HPFS/NTFS  
```> **kansasnoob said:**
> From the Live Desktop go to terminal and run:

```
sudo fdisk -l
```BTW that's a lower case L, post the results here.

---

