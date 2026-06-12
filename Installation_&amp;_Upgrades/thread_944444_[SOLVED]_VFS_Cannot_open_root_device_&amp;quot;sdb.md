---
title: "[SOLVED] VFS: Cannot open root device &amp;quot;sdb6&amp;quot; or unknown-block (0,0)"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by cidhus on 2008-10-11
[FONT="Lucida Console"][/FONT]
I installed Xubuntu 8.04 (64-bit) from a purchased live-DVD on the second drive of a Sun Ultra 20M2 (Opteron x86-64 CPU). The first drive is wholly owned by Solaris 10.

fdisk sees the drives as sda and sdb (they are SATA). The second drive is partitioned so:
.  sdb1 - 500MB VFAT
.  sdb2 - 30GB VFAT16
.  sdb3 - 50GB NTFS
.  sdb5 - 4GB swap
.  sdb6 - 10G ext3 /
.  sdb7 - 192M ext3 /boot
.  sdb8 - 2G ext3 /root
.  sdb9 - 4G ext3 /usr/local
.  sdb10 - 6G ext3 /opt
.  sdb11 - 4G ext3 /var
.  sdb12 - 2G ext3 /tmp
.  sdb13 - 20G ext3 /home
remainder is free. sdb1-3 are not formatted. Since the machine boots from Grub, I did not install the boot loader (it's already on sda).

In Solaris, /boot/grub/menu.lst (for now) has
#####
title Xubuntu
root (hd1,6)
kernel /vmlinuz root=/dev/sdb6 resume=/dev/hda3
init /initrd
#####

I added the soft-links vmlinuz and initrd in the Xubuntu /boot. They already existed in the Xubuntu /. I can boot from the DVD and mount sdb6 etc. just fine. It's how I added the soft-links.

Booting into Xubuntu on the hard disk gives the dreaded kernel panic. The last three lines on boot are:

24.640112] VFS: Cannot open root device "sdb6" or unknown-block(0,0)
24.640161] Please append a correct "root=" boot option; here are the available partitions:
24.640220] Kernel panic - not synching: VFS: Unable to mount root fs on unknown block(0,0)

I've read the Grub manual (twice) and searched these forums. The most common response seems to be to rebuild the initrd image. How would I go about doing that on sdb6 from a live-CD boot? Is that really my problem?

I'm really paranoid about touching the first hard disk from anything other than Solaris. Please keep that in mind.

Thank you.

Herb Coburn

---

### Post by sisco311 on 2008-10-11
try to set the root partition by uuid.

as root type:
```
blkid /dev/sda6
```
or
```
vol_id --uuid /dev/sda6
```to get the uuid of the partition.

here is my menu.lst entry:
> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=**UUID=e75b6319-4a0c-4336-94ad-9c534418f6e7 **ro quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet


---

### Post by cidhus on 2008-10-12
sisco311, thank you for the advice. Unfortunately, it's still
a no go.

Herb

---

### Post by cidhus on 2008-10-13
The problem arose because initrd.img did not load a module required to read ext3 type partitions and the kernel did not have support for journaling compiled in (depends on modules).

The resolution is to makeinitrd with the necessary module or recompile the kernel with support for the journalled file system. A wee bit of difficulty without the devel package and source code, I might mention.

Work around is to re-format the partitions as ext2 during the re-install. Later on I'll experiment with makeinitrd. Proof this works is I'm posting from a new install of Xubuntu booted from the Solaris 10 Grub.

Herb Coburn

---

