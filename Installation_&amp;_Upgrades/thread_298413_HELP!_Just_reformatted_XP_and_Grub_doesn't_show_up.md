---
title: "HELP! Just reformatted XP and Grub doesn't show up!"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by Aazn on 2006-11-12
AAAAH!

I had to reinstall Windows because of DHCP random errors and stuff, it works fine now, but GRUB does not show up and I cannot boot into my Linux partition!

The partition is still there, I can mount it by adding an entry into my /etc/fstab from the LiveCD, the files are still there, but I can't boot into it.

Can someone give me step-by-step instructions on how to put Grub back into my MBR? Preferably without a boot disc, could I do this from the Terminal on the CD? Thanks!

---

### Post by deepwave on 2006-11-12
Boot off a LiveCD.  And with run grub-install /dev/hda assuming your MBR is on that disk.

---

### Post by BLTicklemonster on 2006-11-12
I've never understood what's going on with grub and windows. I had this in c:\boot.ini in one version:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
c:\bootsect.lnx="Ubuntu Linux"

```

and I have no idea about c:\bootsect.lnx because there never was such a thing.

In my present windows, I have this:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
```

What is Aazn talking about?

---

### Post by orb9220 on 2006-11-12
First you need to understand is Grub Does not install to the windows boot.ini. It writes a loader to the MBR MasterBootRecord.

Which is a bit of code to the beginning of the hardrive. If you install windows after ubuntu then windows overwrites that mbr with it's own. It thinks it is the only OS in the world.

You have to reinstall grub to the mbr which will not affect your xp at all. The link is below to do this.

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by BLTicklemonster on 2006-11-12
OIC!

Thanks.

---

### Post by max.diems on 2006-11-12
sper Grub Disk it helpful for a lot of people, too. Try it.

---

