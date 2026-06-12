---
title: "Windows FakeRAID together with Ubuntu mdadm?"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by alanwalterthomas on 2010-08-09
My motherboard has a BIOS feature to support RAID1 for two disks. I know it's FakeRAID but that's what Windows can work with. I've read that Linux's built in softraid mdadm is better so I'd prefer to use that for Linux's own filesystems. Can I enable FakeRAID in the BIOS without it affecting Linux in any way? Is it possible for Ubuntu to read and/or write to the NTFS partition that's raided with the fakeraid?

Also, if running mdadm in RAID 1 how much risk is there of losing data if the computer crashes? Is e2fsck able to repair a filesystem on a RAID 1 setup?

---

### Post by ronparent on 2010-08-10
Windows cannot access a ubuntu software raid. In my opinion the whole issue of trying to use fakeraid in ubuntu is sufficiently perilous without mixing software raid (mdadm) and fakeraid (dmraid) on the same system. I suggess comitting to one or another.

Better is a subjective issue and may be imaterial depending on what you are doing with it.

---

### Post by alanwalterthomas on 2010-08-10
I think I should be able to get read-only access to an ubuntu raid 1 from windows using as I do now with ext2explore, or rather to one of the two disks. Good enough.
I'm still wondering about ntfs3g working when I try to get read or read/write access to my windows partition. Is that possible?

---

### Post by alanwalterthomas on 2010-08-13
Huh, waiting for my new disks, but this
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/442735](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/442735)
suggests BAD THINGS happen if you try to apply mdadm & dmraid to the same disks.
Nutz. Any ideas?

---

### Post by alanwalterthomas on 2010-12-06
I tried it. Didn't work - at all. Might be a coincidence, but immediately after I activiated fakeraid, one of my attached disks, a third that wasn't added to the array, failed. Ran manufacturer tests & it's now a dead disk although it seemed to be in perfect condition before. At least it had a warranty.

My setup now is:
2x WD 640 Caviar Black HDDs.
Installed Win 7 on 100 GB of one.
Used the ubuntu alternate install disk to put a 2x 50GB / softraid (mdm)partition, & then a 450 GB softraid RAID1 partition for /home, then 7 GB Swap. There is some space left on the 2nd drive because windows 7 is on the first. I'm using that to backup documents, pictures, etc from win 7 using Déjà Dup Backup (in repos). Works beautifully.

Note that Windows 7 ultimate has softraid capabilities somewhat like ubuntu, & could have set something up, but didn't trust it.

I tried hard to find a way to install windows ultimate system files on its softraid 0, but it just can't. You can set up a raid 0 partition after install & try to install programs there, but trying to boot to that is a waste of time.

Hope this helps anyone who may have similar needs.

---

