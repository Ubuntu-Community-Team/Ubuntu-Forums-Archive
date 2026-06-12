---
title: "[SOLVED] Overwrote Boot Sector With Windows"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by fitzwell on 2008-04-27
Hi,
When trying to rescue an XP partition, I ran a fixboot command at the Recovery Console, and accidentally applied it to my Ubuntu partition.  Now I can't boot the Ubuntu partition, even though I can mount it from the LiveCD, and can see that Grub is installed and all the files look ok.

Here are the outputs from some of my attempts to fix this:

ubuntu@ubuntu:~$ [B][COLOR="Red"]sudo fdisk -l
[/COLOR][/B]
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028513

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22957   184394070   83  Linux
/dev/sda2           23521       30047    52428127+   7  HPFS/NTFS
/dev/sda3           30048       30401     2843505    5  Extended
/dev/sda5           30048       30401     2843473+  82  Linux swap / Solaris


ubuntu@ubuntu:~$ **[COLOR="Red"]sudo e2fsck -f /dev/sda1[/COLOR]**
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 193365/23052288 files (2.3% non-contiguous), 5334572/46098517 blocks
[B][COLOR="Red"]
grub> find /boot/grub/stage1[/COLOR][/B]
 (hd0,0)
[B][COLOR="Red"]
grub> root (hd0,0)[/COLOR][/B]

**[COLOR="Red"]grub> kernel (hd0,0)/boot/vmlinuz-2.6.22-14-generic boot=/dev/sda1 ro[/COLOR]**

**[COLOR="Red"]grub> initrd (hd0,0)/boot/initrd.img-2.6.22-14-generic[/COLOR]**

Error 16: Inconsistent filesystem structure

I'm at a loss as to what to do next.  I know that Grub can read menu.lst, and it can load the kernel, but kicks me to an initfram prompt.

Any help would be greatly appreciated.

---

### Post by Pumalite on 2008-04-27
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#16](http://users.bigpond.net.au/hermanzone/p15.htm#16)

---

### Post by fitzwell on 2008-04-28
When I run ls /dev/disk/by-uuid/ -alh I don't see the UUID for sda1 like I do in the fstab file.  When I run vol_id /dev/sda1 there is no UUID, and the FS_TYPE is vfat.  Is this the reason for the Inconsistent filesystem structure error, and if so. how would I go about fixing it?

---

### Post by Pumalite on 2008-04-28
Compare:
In Terminal: blkid
/etc/fstab
/boot/grub/menu.lst

The UUID of all drives/partitions must coincide.

---

### Post by fitzwell on 2008-04-28
Well, once I replaced the UUID in menu.lst with /dev/sda1 (and in fstab, too), it booted.  Not sure what stupid Windows did, but there was a disconnect somewhere in Grub Stage 2.  Thanks for your help.

---

### Post by Pumalite on 2008-04-28
You are welcome.

---

