---
title: "grub2 on lvm2"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by neybis on 2011-02-15
Old thread is closed, opening a new one with a little more explanation this time ;)

Okay, so I have a netbook with an 8GB SSD (/dev/sda) and an 8GB SD Card (/dev/mmcblk0). I want to put them on a LV so UNR reads the drive as one 16GB drive. I have followed countless guides, read numerous bug reports, and crawled virtually every website google could throw at me for the last 3 or 4 nights and im stumped. First and foremost, the ubuntu installer has no problems detecting my LV (/dev/mapper/lvm-root), creating a partition table and formating the LV partition as ext4 (/dev/mapper/lvm-rootp1). It installs the OS fine but when it gets to the bootloader it gives an error. I have read you are to install the bootloader onto /dev/sda but the only way past this point in the install is to choose to not install a bootloader but continue anyway. I somewhat expected this although others seem to have no issues with the installer loading the bootloader with /boot being located on an LV. This is where I have tried virtually everything known to my best knowledge and need you help. Here is some output from me trying to install grub2:


```

root@ubuntu:/# update-grub
Generating grub.cfg ...
/usr/sbin/grub-probe: error: no mapping exists for `lvm-rootp1'.

```

```

root@ubuntu:/# less /boot/grub/devices.map
/boot/grub/devices.map: No such file or directory

```

```

root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-probe: error: no mapping exists for `lvm-rootp1'.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

```

root@ubuntu:/# grub-install --modules=lvm /dev/sda
/usr/sbin/grub-probe: error: no mapping exists for `lvm-rootp1'.
/usr/sbin/grub-probe: error: no mapping exists for `lvm-rootp1'.
/usr/sbin/grub-probe: error: no mapping exists for `lvm-rootp1'.
You attempted a cross-disk install, but the filesystem containing /boot/grub does not support UUIDs.

```

```

root@ubuntu:/# blkid
/dev/mmcblk0p1: UUID="LoCZaW-r1cn-e4Bd-vVys-FT9d-Ow39-WHaSMM" TYPE="LVM2_member"
/dev/sda1: UUID="CPn3Vo-yvkZ-RJ2H-1b0a-Xp6y-0nEc-Tf2OSP" TYPE="LVM2_member"
/dev/loop0: TYPE="squashfs"
/dev/sdb1: UUID="2F8D-B53E" TYPE="vfat"
/dev/mapper/lvm-rootp1: UUID="aa5f9db3-90b1-4b10-b579-9202dbd27c55" TYPE="ext4"

```

I appreciate the help and hopefully you guys can relieve my frustration ;)

---

### Post by neybis on 2011-02-16
bump

---

### Post by neybis on 2011-02-16
can anyone help me?? I feel like it is probably something really simple since no one else seems to be having issues now that the bug im experiencing has been fixed.

---

### Post by neybis on 2011-02-17
bump

---

### Post by psusi on 2011-02-17
You don't partition a logical volume.

Also this whole goal is a bad idea.  SD cards are much slower than the SSD.  If you span one fs across both devices, then some files will be fast, and others will be slow, and you have no control over which is which.  It is much better to leave them as separate filesystems so you can manually choose to put large files you don't need high speed access to on the slower device.

---

### Post by neybis on 2011-02-17
very interesting...thank you for your help. I am really not concerned about speed but convienence and have ran into space issues keeping the partitions seperate. For example, my home directory was mounted to the SD card which filled up quickly while the SSD remained with multiple GBs free.

To question your response, how do you install ubuntu on a LV without a partition table? After creating the volume and starting the installation I manually configured the partitions rather than letting ubuntu install onto the SSD as it recommended. When manually configuring the partition I was unable to continue with the install until I created a partition map for the LV which allowed the installer to make the new partition ext4 and install onto it. Can you elaborate on the process? Ubuntu seems to want to create a partition map.

---

### Post by psusi on 2011-02-17
You use the logical volume for the filesystem.  It is the logical equivalent of a partition, not a whole disk.  You don't partition partitions, so you don't partition logical volumes either.

I suggest that you just do a normal installation without LVM entirely onto the ssd ( no separate /home ), then just use the sd card to store large media files and such.  That will be much less confusing.

---

### Post by neybis on 2011-02-17
I cannot thank you enough, I know very little about lvm's and appreciate you pointing out the drawbacks of an lvm on my system. however, the benefits outweigh the costs for myself and so I push forward. ;)

I have got grub2 to install! yay! ubuntu did not complain however when I reboot, I get dumped to a grub rescue prompt with the following error message above it:

error: physical volume pv1 not found.

When an ls is performed I see (lvm-root) (hd0) (hd0,1) (hd1) (hd1,1) so my lv appears to be recognized. I thought it may not be working due to incorrect modules so installed grub with --modules="lvm ext2" since ext2 supports 2/3/4. this however caused (lvm-root) to disappear completely so I went back and installed grub letting it take care of the modules manually. (lvm-root) is back now. if I ls (lvm-root)/ I get the pv error message again and ls'ing anything else gives unknown filesystem for obvious reason. Any tips/clues??

---

### Post by psusi on 2011-02-17
I don't know why it shows an hd1.  Your bios probably can not recognize the sdcard, so neither can grub, hence why it can't find it.

---

### Post by neybis on 2011-02-17
My apologies...I had my USB stick plugged in still. removed it and hd1 went away :P

so that sucks...I guess ill have to settle with a boot partition outside the lvm.

---

