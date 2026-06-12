---
title: "Partion Editor and WinXP install How?"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by TehPeanut on 2011-01-14
Hello All,

Im having some trouble dual booting Ubuntu 10.10 32bit with WinXP
the first problem I'm having is using Partion Editor to resize my Ubuntu install
the option to use it is not available
Any ideas?

Complete Linux Nub here

---

### Post by dino99 on 2011-01-14
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by kansasnoob on 2011-01-14
> **TehPeanut said:**
> Hello All,

Im having some trouble dual booting Ubuntu 10.10 32bit with WinXP
the first problem I'm having is using Partion Editor to resize my Ubuntu install
the option to use it is not available
Any ideas?

Complete Linux Nub here

**Please read this all before beginning!** If any of this is confusing ask for clarification, particularly if you have a more complex partitioning arrangement, boot into your installed Ubuntu and post the output of these two commands:

```
sudo parted -l
```

```
cat /etc/fstab
```

So you're installing XP after installing Ubuntu?

It's fine if you are, I just need to know for sure. As far as using Gparted you'll need to run it from the Live CD, that is choose to Try Ubuntu rather than Install, then you'll find it in System > Administration > Gparted.

NOTE: Backup anything important. There is always some danger of data loss during any repartitioning/installation procedure!

You'll typically need to right-click on the SWAP partition and select swapoff. If it's a typical installation (no special partitions like "/home" or "/boot") then you'd right-click on the main Ubuntu partition and select Resize/Move.

A new window will open so position the mouse pointer over the left end of the partition graphic (you'll see the pointer change to a double arrow) and drag the left end to the right to create a free space for Windows as shown here:

[ATTACH]181069[/ATTACH]

Then click on the Resize/Move button in the lower right hand corner of that window, then click on the green arrow at the top of the main Gparted window and verify by clicking on Apply. Depending on how much space you're freeing up it will take quite a while for that to complete. Do not abort that operation! Be patient! About 30 to 40 minutes (+ or -) is typical!

Once that is complete record the size of the  partitions and unallocated space. Do NOT create a new partition for XP, just leave the space unallocated.

Next just reboot and make sure that your installed Ubuntu still boots, if so it's time to pop in the XP installation disc. Look at **[COLOR="Red"]the page[/COLOR]** in the following link so you'll know what to expect. **[COLOR="Red"]Look only at that one page, the instructions for Grub are NOT correct![/COLOR]**

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4)

Choose only the **unpartitioned space**!

Once Windows is installed you'll no longer be able to boot Ubuntu but first try booting Windows just to be sure it installed correctly and then boot your Ubuntu Live CD again. Once you're in the Live Ubuntu session run the command:

```
sudo fdisk -l
```

BTW that's a lower case L. I'd expect to see something similar to this:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00082dba

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Red"]/dev/sda1[/COLOR]**               1        9197    73872384   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda3            9197        9328     1048576    7  HPFS/NTFS
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Partition table entries are not in disk order
```

You can see in the System column to the right it displays the filesystem type (HPFS/NTFS is typically Windows, your Ubuntu root partition should be identified as Linux). I know in that example my Ubuntu root partition is /dev/sda1 as highlighted above. **Based on that sample output** you'd need to copy-n-paste the following commands:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

Hopefully that's it. If not don't panic! Just post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2011-01-14
Deleted due to duplication.

---

