---
title: "using 10.10 home.disk to revert to 10.04"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by andreasbuykx on 2010-11-08
Hi all,

I have installed wubi 10.04, and tried to upgrade to 10.10. After the upgrade I couldn't boot ubuntu at first but with the wubildr fix that has been posted my ubuntu seems alive, somewhat. During booting some messages are shown briefly (I don't know how to capture them), but I then can log in and the system seems fairly OK, except that intermittently it hangs (only cursor movement works, nothing else), mostly when I'm using firefox. 

I don't have that much data in my /home area except for the configurations of firefox, thunderbird etc. What I would like to try is to backup my c:\ubuntu\disks\home.disk, uninstall wubi (originally 10.04, now 10.10), reinstall wubi 10.04 from scratch and then restore my home.disk as [explained]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20create%20a%20virtual%20disk%20in%20Windows?") in the wubi guide.

Is this possible at all? Is it possible to use the /home.disk that I created with 10.10 with a fresh 10.04 wubi install?

Thanks for your help.

Andreas

---

### Post by bcbc on 2010-11-08
I'm not sure - but I'm in test mode today so I'll try it. 

Result: it appears to work based on my test - though I guess you'll lose any settings that are outside of /home and you'll need to reinstall all the apps you had before. Caveat - I installed the 10.10 some time today so haven't done a lot of customizing.

By the way, I have some reservations about that script to create a separate /home virtual disk. Reason being is that it creates a sparse file, and in my mind this can lead to excessive fragmentation.
e.g. I've created a separate /home of 3GB but you can see it's currently only occupies 174464 bytes, although it can be expanded to 3GB:
```
bcbc@ubuntu:~$ du /host/ubuntu/disks/home.disk
174464    /host/ubuntu/disks/home.disk
bcbc@ubuntu:~$ du /host/ubuntu/disks/home.disk --apparent-size
2930665    /host/ubuntu/disks/home.disk

```If you want to preallocate the whole file then edit the script before running it:
Before:
```
dd if=/dev/zero of="$virtual_disk" bs=1MB count=1 seek="$size_mb"
```After:
```
dd if=/dev/zero of="$virtual_disk" bs=1MB count="$size_mb"
```
If you're editing the script, you might as well change it to create /home as ext4 instead of ext3 (ext4 is used these days by default - since karmic). It shouldn't hurt either way. (Lines 51 and 54 need to be changed)

Also move the home.disk file OUTSIDE of the c:\ubuntu directory before uninstalling/installing 10.04.1 or it will be deleted.

After installing 10.04.1, I booted into it and just manually moved the new /home and edited the fstab, then rebooted to windows to move back my home.disk. I made a typo and had to manually fix fstab while booting :). It might be safer to repeat the procedure (to create the separate home on the new install) and then just copy over the new home.disk with the one you backed up.

Anyway - as I said - it's hardly a rigorous test, but nothing died. I had my maverick desktop background, my icons I copied to the panel, and when I opened firefox it opened all my saved tabs the way I had them when I shut down maverick. So the firefox bit seemed fine.

(I also used the default script - didn't edit it the way I suggested here. I still think preallocation of the full virtual disk is better.)

---

### Post by andreasbuykx on 2010-11-09
Thanks for the extensive reply. I'm definitely going to follow your advice. Your comments about the home.disk file come too late for me, I've already created that file. I suppose defragmentation of the file with e.g. mydefrag will help?

I expected that programs will always record user-settings in /home. What kind of settings go elsewhere?

---

### Post by bcbc on 2010-11-09
Most data is in /home. I have some customized .conf files that are floating around somewhere. samba, openssh, grub, etc. Depending on the mail client you use there could be data in /var/mail although it seems most move it to /home. 
It's good to be cautious.

Regarding defragging - it's probably a good idea to defrag windows, but the actual home.disk will expand only when space is required, so I don't think it will prevent future fragmentation. But maybe I'm making too big a deal about it - I haven't noticed anyone complaining about it :).

---

