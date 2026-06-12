---
title: "Can't boot ubuntu dual boot with xp"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by mikiowoko on 2010-05-24
Have a computer with xp sp3.
I tried an ubuntu install and the mbr seemed to be trashed.
Reformatted the drive and reinstalled windows xp and easyBCD
Reinstalled ubuntu without GRUB

here's the present configuration:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Device    Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30618   245931254+   7  HPFS/NTFS
/dev/sda2           30618       60802   242454529    5  Extended
/dev/sda5           30618       59864   234925056   83  Linux
/dev/sda6           59865       60802     7528448   82  Linux swap / Solaris

```
What I think I need to do is install grub in /dev/sda5, but I'm not sure if that's correct, and regardless, I'm not sure how to do that.

---

### Post by darkod on 2010-05-24
You should have asked for help to repair the first install, not to format it. Since you didn't install grub at all, it's more difficult to add it later when the config files don't exist.
Also, if you are installing 10.04 it comes with grub2 and depending which version of EasyBCD you installed, it might not support grub2 (only ver2 and above supports it).

I would recommend using the ubuntu cd in live mode, and using Gparted to delete your ubuntu partitions, leave just /dev/sda1. After that install again with Use Largest Available Free space, and let it install grub2 to the MBR of /dev/sda.

If there are any issues with grub and the mbr, boot the cd in live mode, and post here for help. But I think it will work out jut fine.

---

### Post by mikiowoko on 2010-05-24
I have the latest version of easyBCD.

I initially let the ubuntu install in the largest free space and ended up with a trashed mbr which is why I started over. 

If I boot in live mode, I think there should be a way to install lilo or grub/grub2 in sda5 and let easyBCD handle the boot. Rather than a whole new install.

I guess I could start over.:rolleyes:

---

### Post by darkod on 2010-05-24
There is a way but I don't know the full commands when it wasn't installed previously.

---

### Post by oldfred on 2010-05-24
As Darko says it is not recommended:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
grub-setup -v /dev/sda6
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force

---

### Post by mikiowoko on 2010-05-24
Would lilo be a better alternative? 

I am not looking to mess with the mbr. just need to load linux, easybcd will grab the boot vector, just need a place to send it.

---

### Post by oldfred on 2010-05-25
I believe the lilo boot loader works like windows. It looks for a partition with a boot flag and jumps to the PBR partition boot record or first sector.

You can force grub2 into the partition. What is the problem with using grub2 as the boot loader in the MBR? Only a few users with win7 software that (erroneously) writes into the MBR and corrupts grub2 have issues, just about everything else that users had as issues before have been solved. I never had any issues with grub2 other than it was different and had to learn a new way to update and customize.Old dogs can learn new tricks.:)

---

### Post by mikiowoko on 2010-05-25
I'm hesitant to try it again, first time it hosed the mbr- fixboot and fixmbr could not repair for some reason.:(

---

