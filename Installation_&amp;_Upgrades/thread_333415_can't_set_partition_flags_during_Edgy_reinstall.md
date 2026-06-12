---
title: "can't set partition flags during Edgy reinstall"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by drx4 on 2007-01-07
I'm trying to reinstall Edgy and can't figure out how to change the partition flags.

My first install completed and left the XP partition intact.  After that, the partition table was as follows:

    Partition    Filesys      Size       Used     Unused  Flags
    /dev/sda1      fat32    15.63 GB   9.47 GB   6.15 GB  lba
    /dev/sda2      ext3     56.48 GB   1.01 GB  55.47 GB  boot
   */dev/sda3    extended    2.42 GB       -         -
      /dev/sda5 linux-swap   2.42 GB       -         -

The system came up fine.  As far as I could tell, though, the X configuration was a disaster (see bug #77765).  So I wanted to reinstall Edgy and try again.

On the reinstall, both automatic and manual installation show this:

    Partition    Filesys      Size       Used     Unused  Flags
    /dev/sda1      fat32    15.63 GB   9.47 GB   6.15 GB  boot,lba
    /dev/sda2      ext3     56.48 GB   1.01 GB  55.47 GB
   */dev/sda3    extended    2.42 GB       -         -
      /dev/sda5 linux-swap   2.42 GB       -         -

How can I get the boot flags back the way they were?  I've read that I can't do this with gparted, and that was true as far as I could tell.

Thanks.

---

