---
title: "Incorrect filesystem size after clone"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by PiPBuntu on 2010-03-17
Question:Several months ago I upgraded my hard drive on a dual boot machine (xp & U9.10 - both 64bit) from approx 80gb to 250gb. I chose to use DriveClone from windows to clone the old drive directly to the new drive. Operational everything works fine. the problem is the Ubuntu HD size went from around 10GB to approx 150Gb, but the filesystem only recognizes approx. 10GB as the total available capacity. I just tried to reinstall Ubuntu without reformatting and only recovered a few GB's. GParted reports the proper partition size. Is there any way I can correct this problem? It's not a big issue...I thought I would check here first before I reformatted the partition. The pre-boot disk check ran and reported no errors but the file system is still not seeing the unused GB's.

---

### Post by srs5694 on 2010-03-17
The Windows tool probably did a byte-for-byte copy of the Linux filesystem, which would have kept the *filesystem* at the same size, even though it was in a bigger *partition*. It'd be like taking a loaf of store-bought bread out of its bag and putting it in a huge garbage bag; the bag's bigger, but the bread won't expand to fill that space.

This is easily corrected, though. Use the text-mode resize utility for your filesystem. If you're using ext2fs/ext3fs/ext4fs, it'll be resize2fs:

```

sudo resize2fs /dev/sda5

```

Change /dev/sda5 to whatever the appropriate device is for your Linux system. This operation shouldn't take very long. It will resize the filesystem to fill the partition. Some resize utilities require the filesystem to be unmounted before they'll work, but resize2fs will increase the size of a filesystem while it's still mounted, so you shouldn't need to shut down if you're using ext2/ext3/ext4.

---

### Post by PiPBuntu on 2010-03-18
Thanks [B]srs5694! 
The resize2fs command corrected the problem. It failed to completely execute from a terminal. For some reason the computer froze up and was unresponsive (no HD activity). I booted into rescue mode and ran it from there and now the free space is approx 132GB's. Thanks again!
[/B]

---

### Post by srs5694 on 2010-03-18
Freezing up is not good. I've resized ext3 filesystems "live" with no problems, but it sounds like that feature may be buggy. I'll be sure to keep that in mind in the future, and only do such resizes offline whenever possible. I'm glad it worked for you in the end, though.

---

