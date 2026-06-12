---
title: "Two HD's, one MBR and the other GPT?"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by expelledboy on 2010-07-26
I want to use GPT, but still use TinyXP.

Can someone help or point me to a guide to getting one harddisk working with a MBR and a second working with a GPT?

---

### Post by oldfred on 2010-07-26
I just converted one of my 160GB drives to GPT and installed Lucid & then changed to Maverick to test.

I just used gparted but changed to use gpt and did create a bios_grub partition with gparted.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.
You can do this in gparted or:
sudo parted /dev/sda set <partition_number> bios_grub on
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown


I did find that while it booted Ubuntu just fine in the gpt it would not work with the MBR drive until I added:

Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.
or:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

---

### Post by expelledboy on 2010-07-29
Do you think it was worth the effort?

---

### Post by oldfred on 2010-07-29
I have not used it much. It now has Maverick in it but I only boot it occasionally. I wanted to understand a little more about gpt but without new motherboard will not be able to experiment with efi. I do not 'see' any difference. But every partition is primary, but you need primary's for windows and older windows does not work with gpt.

I consider gpt the future as msdos/MBR has a max of 2GiB. I am not sure if the new 4K drives are a work around or not.

---

