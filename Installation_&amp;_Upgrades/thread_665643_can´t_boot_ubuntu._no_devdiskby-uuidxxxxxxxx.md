---
title: "can´t boot ubuntu. no /dev/disk/by-uuid/xxxxxxxx"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by rmx on 2008-01-12
Hello.

Once, I made a copy of my ubuntu partition with acronis software to an external drive.

After messed my ubuntu, I copied the backup to original partition.

After booting, the system  halts for around five minutes warning me about clocksource tsc unstable.

then it says that could not find the /dev/disk/by-uuid/xxxxxx device, and jumps into a mini console which I never knew about. (with a strange prompt)

I'm not sure what is a uuid device and how is it made.

As a newbie, I guess uuid could be a partition identifier stored on Super Block.
And maybe acronis made a new one when coping the partition.

I don't know if this makes any sence.

What do you think about all this?

how can I solve the problem?

thank you

rmx

---

### Post by richardjennings on 2008-01-12
I would try reinstalling grub onto the mbr.

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by rmx on 2008-01-12
sorry 
duplicated:(

---

### Post by rmx on 2008-01-12
thanks for your suggestion richardjennings.

I followed the second sugestion posted on the link [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

but nothing change.

I'll try to describe the error and the last line before it:

[13.068000] clocksource tsc unstablle (delta = - .....)  /*hangs on this line for about 5 mins!!!*/
Done.

check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev


ALERT! /dev/disk/by-uuid/..... does not exist. dropping to a shell!

(initramfs)

---

### Post by richardjennings on 2008-01-12
To find the uuid of the harddisk you can use 

```
blkid
```

appending ```
notsc
``` to the kernel line in grub should help with the clocksource error.

Have you restored ubuntu to the same drive it was originally installed onto? Check that the uuid values in fstab are correct.

```
cat /etc/fstab
```

---

### Post by rmx on 2008-01-13
> **richardjennings said:**
> To find the uuid of the harddisk you can use 

```
blkid
```
[B]
I done.
output:[/B]

[HTML]/dev/sda1: UUID="46F1AEFC4551F0E6" LABEL="windows" TYPE="ntfs" 
/dev/sda5: LABEL="FAT32" UUID="E8A1-F8E5" TYPE="vfat" 
/dev/sda6: UUID="e1fe5b2e-2e10-fc46-df86-1ab4b5d33a12" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="6ff8eaeb-885a-4619-8d2c-9db092104010" 
/dev/sdb1: LABEL="USBRMX" UUID="F879-1D6C" TYPE="vfat"[/HTML]

appending ```
notsc
``` to the kernel line in grub should help with the clocksource error.

**I append it in /boot/grub/menu.lst . And changed the corresponding uuid to the e1fe5b2e-2e10-fc46-df86-1ab4b5d33a12.**

Have you restored ubuntu to the same drive it was originally installed onto? Check that the uuid values in fstab are correct.

```
cat /etc/fstab
```
[B]I changed from the old value to the new value.
[/B]

It didn't work out, so I'll try to put the outuput where it stoped.

```

[4.136000] K journald starting. commit interval 5 seconds.
[4.136000] EXT3-fs: mounted filesystem with ordered data mode.

Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.

```

and system hangs without any prompt.

With live-cd I tried to cat /scripts/local-bottom and /scripts/init-bottom, but I don't even have /scripts/.

Thank you.
rmx

---

### Post by richardjennings on 2008-01-14
The problem seems to be that the filesystem uuid on /sda6/ is different to that of the drive/ partition.

To find this out for sure, 

```
sudo tune2fs -l /dev/sda6 | grep UUID
```

should give the same uuid as

```
blkid
```

if it doesn't, you can use tune2fs to change the filesystem uuid.

```
sudo tune2fs -U e1fe5b2e-2e10-fc46-df86-1ab4b5d33a12 /dev/sda6
```

---

### Post by dbasemanager on 2008-05-29
Hi 

I had a similiar issue. My UUID was different returned by  blkid command and in /dev/disk/by-uuid. I updated my uuid as richardjennings mentioned to the one returned by /dev/disk/by-uuid

Now everything looks fine. Anyone has got any idea why /dev/disk/by-uuid and uuid returned by blkids were different?

dbase

---

