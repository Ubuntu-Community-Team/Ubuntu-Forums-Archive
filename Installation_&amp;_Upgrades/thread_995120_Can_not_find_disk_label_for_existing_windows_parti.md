---
title: "Can not find disk label for existing windows partition during installation"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by chjustc on 2008-11-27
Hi there,

I bought a new desktop (64-bit CPU) that had windows Vista as the only operating system on it.  In windows Vista, I could only see C:/ drive. Last night, I tried to install Kubuntu 8.10 for 64-bit machines on it.

The installation disk loaded OK. When the installation came to the part of partitioning hard disk, it found /dev/sda and /dev/sdb.  But, there was no partition table on either of them.  All the space was free. I could not see any information about the existing windows partition.

Then, I exited the installation, opened a shell prompt, and ran
```
ubuntu@ubuntu:~$ sudo fdisk -l
```
I got the results as follows,
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76534   614759323+   7  HPFS/NTFS
/dev/sda2           76535       77826    10377990    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38fb89b5

Disk /dev/sdb doesn't contain a valid partition table

```

I guessed the windows Vista partition was on /dev/sda. But, when I went back to the installation again, I still could not see any existing partition.

I was going to install Kubuntu on /dev/sdb and left /dev/sda alone. But, as a precautionary attempt, I want to ask you whehter this is the right thing to do.  Any suggestions about why I could not see existing partition during installation and how to fix it.

By the way, I installed ubuntu several times on my own laptop and other desktops without any problem.  I was always able to find the existing (windows) partition. My goal was always keeping both windows and ubuntu. So, I always left the windows partition alone or just cut the size of it from the end.  But, this time, I don't know what is going on.  I don't want to break anything on the windows partition.

Thanks.

---

### Post by chjustc on 2008-11-27
Can anyone help me?

---

### Post by Aussieartist on 2008-12-31
Hi,

I don't know if this is of any help but I'm having a similar problem - sort of... I can't see a missing partition. My HDD is 320gb and when I installed Ubuntu (Whole disk option, not dual boot) I only got a partition of about 285gb... I suspect the missing space is my factory install Vi$ta recovery disk, of course the recovery function does not work (not that I want or need it)... anyhow another thread suggested this diagnostic:

> cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt


I did it and got all kinds of info, still working through it...
But it did tell me:
 => Drive sdb does not have a valid partition table.
 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.

Don't know if this will help you but worth a try?

Cheers
Aussie

---

