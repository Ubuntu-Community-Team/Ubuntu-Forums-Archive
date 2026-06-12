---
title: "Yet Another Dual Booting Problem"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by akcom on 2006-07-02
I wanted to dual boot my computer with the newest version of Ubuntu, so I proceeded to format, install windows, and then tried installing Ubuntu.  Everything went smoothly until the final reboot.  When the computer started up, grub died at step 1.5.  I then tried booting into the live cd and then doing "sudo grub-install /dev/hda" and "sudo grub-install hd0" neither of which worked.  They both gave the following error message: 
"Could not find device for /boot: Not found or not a block device."

I then tried using "sudo grub" then root (hd0,1) (my linux partition) then install hd0.   Grub reported it was installed successfully but yet again, did not function properly.

Any ideas?

btw, heres my desktop setup
hd0:
90 GiB NTFS partition
89 GiB ext3 partition
1 GiB swap partition

hd1:
40GB FAT32

thanks in advance for the replies.

---

### Post by confused57 on 2006-07-02
[QUOTE=akcom]I wanted to dual boot my computer with the newest version of Ubuntu, so I proceeded to format, install windows, and then tried installing Ubuntu.  Everything went smoothly until the final reboot.  When the computer started up, grub died at step 1.5.  I then tried booting into the live cd and then doing "sudo grub-install /dev/hda" and "sudo grub-install hd0" neither of which worked.  They both gave the following error message: 
"Could not find device for /boot: Not found or not a block device."

I then tried using "sudo grub" then root (hd0,1) (my linux partition) then install hd0.   Grub reported it was installed successfully but yet again, did not function properly.

Any ideas?

btw, heres my desktop setup
hd0:
90 GiB NTFS partition
89 GiB ext3 partition
1 GiB swap partition

hd1:
40GB FAT32

thanks in advance for the replies.[/QUOTE]

I really don't know what the grub died at step 1.5 is...

Try booting up with the Live CD, opening a terminal, and check the output of:
```
fdisk -l
```
The -l is a small "L".

When you first installed Ubuntu and rebooted, did the grub menu display with the options of Windows or Ubuntu?  Were you able to boot either OS?
Here's someone who's having the same sort of problem:
[http://www.ubuntuforums.org/showthread.php?t=206330](http://www.ubuntuforums.org/showthread.php?t=206330)

---

### Post by akcom on 2006-07-03
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12395    99562806    7  HPFS/NTFS
/dev/hda2   *       12396       24651    98446320   83  Linux
/dev/hda3           24652       24792     1132582+   5  Extended
/dev/hda5           24652       24792     1132551   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4162    33431233+   c  W95 FAT32 (LBA)
/dev/hdb2            4163        4865     5646847+   f  W95 Ext'd (LBA)
/dev/hdb5            4163        4865     5646816    b  W95 FAT32

```

I did not even get a GRUB menu.

---

