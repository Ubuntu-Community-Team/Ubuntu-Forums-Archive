---
title: "Broke Windows Vista partition with GParted"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by andycs on 2010-05-22
So far I've been dual-booting Vista and Intrepid, and I decided I'd shrink down the Linux partition a bit, expand the Windows partition and reinstall Ubuntu fresh from a Live CD. I booted up from a Live CD, mounted the old Linux filesystem to check that I hadn't missed any documents to back up before I wiped the partition, and then cued up the relevant operations in GParted.

The key mistake I made was not to unmount the old Linux partition first, which led GParted to bug out and, apparently, stop my Windows partition from working. GParted no longer recognises the partition as NTFS - it tells me it's an unknown filesystem, and refuses to move or resize it.

sudo fdisk -l recognises the partition as HPFS/NTFS. Running chkdsk from a Vista recovery disk has been, so far, unsuccessful. What else can I do to either make the partition bootable again, or at least access it from Linux so I can pull my files off?

---

### Post by dino99 on 2010-05-22
[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

in any case you can use formating tools on an active hdd without huge risks :(

---

### Post by darkod on 2010-05-22
Not sure, but you can look into testdisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

