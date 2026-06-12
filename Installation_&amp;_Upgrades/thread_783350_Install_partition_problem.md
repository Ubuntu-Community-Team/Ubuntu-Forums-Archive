---
title: "Install partition problem"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by Hamstermerc on 2008-05-05
I've been using the Wubi install of Ubuntu for a couple of weeks now and i've decided i'd like to fully install it in a separate partition. I downloaded the Ubuntu disk image and burnt it to a cd.(I did the md5 check or something to check it was all ok) I can boot from cd fine but at the partition option i begin to have problems. I tried the guided install and that didn't work saying the partition could not be created.

I also tried a manual partition to resize the ntfs drive with windows on it but again same problem. Could be something to do with having the wubi install on windows or not?

I'd like to keep windows on a separate partition rather than just have ubuntu until i feel completely comfortable with it. Also i know that the wubi option is still a safe install its just i'd rather have it separate to windows.

Any help would be much appreciated

---

### Post by gdelta9 on 2008-05-05
well i had more or less the same problem.What i have been told and what work perfectly for me was to download and burn the gparted live cd and then prepare the HD's with gparted live cd for the ubuntu installation to follow

---

### Post by Don1500 on 2008-05-05
Two disks you should have on your desk during any installation: G-Parted and "The Ultimate Boot Disk"
Both available via a quick Google search.

---

### Post by Pumalite on 2008-05-05
Gparted is fine if you have XP, but with Vista, you can only partition with the Vista partitioner and provide some free 'unallocated' space for Ubuntu first. Then you can use Gparted to make partitions in that space if you want.

---

### Post by Hamstermerc on 2008-05-06
Thanks very much will try the Gparted live CD asap

---

