---
title: "Ubuntu 20.04 ZFS install option"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by nethfel on 2020-04-24
Hi all,

I was messing around with Ubuntu 20.04 in a VM and decided to try out the ZFS install option.  I setup 4 VHDs in the VM to see if the install would allow me to select a raidz level, and/or select which drives to use.  So, I did the basic install, selecting advanced and use ZFS but seemed to only get an option to select which drive I wanted to use (unless I misread the instructions) instead of multiples.  So now I have the system setup with a zpool of a single drive that doesn't appear to be set for anything other than just a single disk in a ZFS pool (not even a degraded mirror) - did I miss something?  Sorry for the seemingly stupid question, but it's my first time trying an Ubuntu install with ZFS :)

---

### Post by dino99 on 2020-04-24
Sorry no zfs skills myself; but i am able to google around :p

 [https://ubuntu.com/tutorials/setup-zfs-storage-pool#1-overview](https://ubuntu.com/tutorials/setup-zfs-storage-pool#1-overview)
[https://vitux.com/how-to-set-up-a-zfs-storage-pool-on-ubuntu/?__cf_chl_jschl_tk__=8410a988d26edd2d16feac9ece81773398e24ff8-1587735706-0-ATWzxOD29N9WRCrfEGOAEYw-bkVqOGtX_lBhzfWo8wKIFUv5npy-lmGlyUq8AQzukzi7xQuQTPUXMZThER7C0UuXOsfOZB6JIHLYuvIs164L5_NS3IbEDw9Ek9-qj3gn-m9yEQfmxnoGSc6zu5zrCf1Wftg4GhVWXIBaoGFx3VzyHeF1qYOVM3I6Anr7FWKbotLb5Kwcomgv1nJL79NDDcBhX0_XbqOxatkWODEYn3I8KP6G5qz5NqXApjkiR_nHGyT_3ARUP8TubUlEnqXq6gxDffBU_APtD6bVD72OALJ3l7w_4juakNlwUfzopDNC2Ls94vx1475wnGxVLTZdLRnHobcgSTrXa3TyZc-NMf-bSNxkzgPKlq3IlV848vfT96eb7Sx8cVxzPz98U9jPKow](https://vitux.com/how-to-set-up-a-zfs-storage-pool-on-ubuntu/?__cf_chl_jschl_tk__=8410a988d26edd2d16feac9ece81773398e24ff8-1587735706-0-ATWzxOD29N9WRCrfEGOAEYw-bkVqOGtX_lBhzfWo8wKIFUv5npy-lmGlyUq8AQzukzi7xQuQTPUXMZThER7C0UuXOsfOZB6JIHLYuvIs164L5_NS3IbEDw9Ek9-qj3gn-m9yEQfmxnoGSc6zu5zrCf1Wftg4GhVWXIBaoGFx3VzyHeF1qYOVM3I6Anr7FWKbotLb5Kwcomgv1nJL79NDDcBhX0_XbqOxatkWODEYn3I8KP6G5qz5NqXApjkiR_nHGyT_3ARUP8TubUlEnqXq6gxDffBU_APtD6bVD72OALJ3l7w_4juakNlwUfzopDNC2Ls94vx1475wnGxVLTZdLRnHobcgSTrXa3TyZc-NMf-bSNxkzgPKlq3IlV848vfT96eb7Sx8cVxzPz98U9jPKow)
[https://askubuntu.com/questions/1189862/how-do-you-automount-additional-pools-with-a-zfs-root](https://askubuntu.com/questions/1189862/how-do-you-automount-additional-pools-with-a-zfs-root)
[http://manpages.ubuntu.com/manpages/focal/man8/zpool.8.html](http://manpages.ubuntu.com/manpages/focal/man8/zpool.8.html)

---

### Post by nethfel on 2020-04-24
Although I appreciate the google searches (I honestly already honestly had several of those) unfortunately, they are mostly covering earlier versions of Ubuntu where it didn't have the ZFS option through the install tool.  I'm looking to understand the baked in install ZFS option that is available and how it defaults.

---

### Post by dino99 on 2020-04-24
an other one (in case it helps)  [https://arstechnica.com/information-technology/2019/10/a-detailed-look-at-ubuntus-new-experimental-zfs-installer/](https://arstechnica.com/information-technology/2019/10/a-detailed-look-at-ubuntus-new-experimental-zfs-installer/)
a more recent one [https://arstechnica.com/gadgets/2020/03/ubuntu-20-04s-zsys-adds-zfs-snapshots-to-package-management/](https://arstechnica.com/gadgets/2020/03/ubuntu-20-04s-zsys-adds-zfs-snapshots-to-package-management/)

---

### Post by nethfel on 2020-04-24
Yup, obviously my googlefoo isn't great this morning.  Although not exactly what I was hoping to learn, it does explain a few things including that their install implementation of ZFS doesn't appear to offer any initial redundancy settings (or lack there of).  At least now I know the path I need to take to actually get some redundancy :D

---

