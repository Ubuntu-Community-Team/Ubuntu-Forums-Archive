---
title: "Missing Operating System after trying to upgrade to Ubuntu 11"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by fingersales on 2012-04-14
Hello there!

After trying to upgrade from Ubuntu 10.04 to 11, the upgrading process  stopped when running and then I got an "out of disk, grub rescue"  message when booting.

After running Boot Repair, I got [these results]("http://paste.ubuntu.com/927387/"): [http://paste.ubuntu.com/927387/](http://paste.ubuntu.com/927387/).

Now I get "**Missing Operating System**" when trying to boot.

Bellow I show some results from some commands I gather from help foruns, but I still reached no solution.

Could you please help me? Any enlightment will be very helpful!

[LIST]
[*]Disk Utility says "Disk has a few bad sectors". When trying to run the Self-test I get "FAILED (Read)"
[/LIST]

[LIST]
[*]Here we have what Gparted says about the /dev/sda1 partition (ext4):

    Flags: boot
    Status: not mounted
    Warning:
    e2label: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
    Couldn`t find valid filesystem superblock

    Unable to read the contents of this filesystem!
[/LIST]

[LIST]
[*]From
    sudo fdisk -l
    I got:

    Disk /dev/sda: 320.1 GB, 320072933376 bytes
    255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x000e0596

    Device Boot Start End Blocks Id System
    /dev/sda1 * 2048 607428607 303713280 83 Linux
    /dev/sda2 607430654 625141759 8855553 5 Extended
    /dev/sda5 607430656 625141759 8855552 82 Linux swap / Solaris

    Disk /dev/sdb: 320.1 GB, 320072933376 bytes
    255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x000c3c41

    Device Boot Start End Blocks Id System /dev/sdb1
    * 63 625137344 312568641 c W95 FAT32 (LBA)
[/LIST]

[LIST]
[*]and from
    sudo fdisk /dev/sda1
    I got

    fdisk: unable to read
    /dev/sda1: Inappropriate ioctl for device`
[/LIST]

[LIST]
[*]From
    sudo mount /dev/sda1 /mnt
    I got:

    mount: wrong fs type, bad option, bad superblock on /dev/sda1,
    missing codepage or helper program, or other error
    In some cases useful info is found in syslog - try
    dmesg | tail or so
[/LIST]

[LIST]
[*]From
    sudo update-grub
    I got:

    error: cannot read from `/dev/sda'.
    /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
[/LIST]

---

### Post by nothingspecial on 2012-04-16
*Thread moved to **Installation & Upgrades**.*

---

### Post by darkod on 2012-04-16
OK, first boot into live mode with the cd, and try to check the partition with:
sudo fsck /dev/sda1

DO NOT mount it first, it needs to be unmounted for the fsck.

Note that even if that repairs some errors, it still might not boot because the upgrade was interrupted. But there is a way to continue that later. First do the fsck.

---

