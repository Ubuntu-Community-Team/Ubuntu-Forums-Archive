---
title: "installating ubuntu in dual boot"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by bchou20 on 2010-09-10
I've windows XP and fedora 5 in dual booting system. Now I want to install ubuntu CD version in place of fedora. when I want to boot my system inserting ubuntu on the drive, the option 'installing ubuntu' does not function. Please help me, how to do that? Partition: Windows 80 GB, Fedora 80 GB.

---

### Post by Mark Phelps on 2010-09-11
Boot from an Ubuntu Live CD.

Ensure that the Fedora partition is not mounted.

Use GParted to reformat the Fedora partition to Ext4.

Now, you should be able to install Ubuntu in its place.

---

### Post by rory526 on 2010-09-11
maybe the cd isn't good.

when you download the iso, make sure the md5sum is the same as on the hashes page.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, when you burn the cd, burn it at the slowest speed available.

---

### Post by Rubi1200 on 2010-09-11
> Ensure that the Fedora partition is not mounted.

You also need to unmount the swap partition: right-click > Swapoff

Then, as suggested above by Mark Phelps.

---

