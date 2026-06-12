---
title: "Encrypted filesystem - problem with server installation."
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by linuxbun on 2007-09-12
[https://help.ubuntu.com/community/EncryptedFilesystemHowto8](https://help.ubuntu.com/community/EncryptedFilesystemHowto8)

I am following the above tut to have an encrypted filesystem. I have 2 hard drives. I installed windows to the first hdd (which I had to make the the first bootable hdd) then I installed 7.04 server edition as directed in the tut to the second hdd (before installation, I then made this hdd the first bootable hdd.

I installed server and partitioned my hdd as the tut directed

....with the exception that I put 100mb boot as "/boot", then named the rest as "/hda2"  "/hda3" etc and made the rest of the space "/" as their mount points. (If I didn't do this, it wouldn't let me proceed with the installation.

My fdisk looks like:
```

Device Boot
/dev/hda1 bla bla bla (windows drive)

Device Boot          Start          End          Blocks              Id          System
/dev/hdd1                1              12           96358+          83           Linux
/dev/hdd2               13            255         1951897+       83           Linux
/dev/hdd3               256          1471        9767520+      83           Linux
/dev/hdd4               11472       9729       66332385+     83           Linux


```

When I try...

```
luksformat -t ext3 /dev/hdd3
```

It just gives me back....

```

[ 1497.971909] devuce-mapper: tableL 254:0: crypt: Device lookup failed

Failed to setup dm-crypt key mapping

Check kernal for support for the aes-cbc-essiv:sha256 cipher spec and verify tat /dev/hdd3 contains at least 133 sectors.

Failed to write to key storage.

Command failed.

Could not creat LUKS device /dev/hdd3 at /urs/sbin/luksformat line 53
```

Any ideas? I've been on it for hours :confused:

---

