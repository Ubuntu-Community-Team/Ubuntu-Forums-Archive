---
title: "[Installation/Partitioning] Partitioner reporting an incorrect drive configuration..?"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by BetaguyGZT on 2008-05-20
Hi all, it's been a while since I posted, and even longer since I've asked for some assistance.

I'm installing 8.04 from USB drive (following this excellent how-to [**here**](http://kmandla.wordpress.com/2006/12/11/install-ubuntu-from-usb/)). The partitioner is displaying my partitions like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=70889&stc=1&d=1211302318[/IMG]

Which is **not** correct.

As you can see in the above screenshot, the partitioner is showing my 120gb **storage** drive as sda1, when it **should** be reporting it as hda1 (since it's on an IDE channel). In fact, the above storage drive is **not** a boot device, according to my bios settings (as intended). Instead, the 80gb SATA drive (which **should** be reporting as sda1) is listed as sdb1 -- and mind you, in my bios settings **it** is the first boot device after my USB and DVD-ROM.

I have WindowsXP installed, and I want to dual-boot. Two attempts at installing Ubuntu using WUBI resulted in the now well-known 'device not found' error, and I was required to do the fixboot/fixmbr thing to get XP back.

As you can see, I've got free space set up for Ubuntu on "sdb1". I'd appreciate some manual partitioning instructions (since my own attempts in the past **never** worked) for ext3 and swap, along with instructions on installing GRUB. I don't want to hose XP or my storage drive, and I'm concerned about doing **both** if I go ahead and do what I **think** is the proper course of action.

Thanks for your attention. I'll remain on the LiveCD for a while until I get some input.

---

### Post by prshah on 2008-05-20
> **BetaguyGZT said:**
> 
As you can see in the above screenshot, the partitioner is showing my 120gb **storage** drive as sda1, when it **should** be reporting it as hda1 (since it's on an IDE channel). 
 the 80gb SATA drive (which **should** be reporting as sda1) is listed as sdb1 -- 

In ubuntu, all IDE drives are treated as scsi subsystem drives; so what you see is _normal_.

---

### Post by BetaguyGZT on 2008-05-20
Alright... so I can go ahead and install to sdb and it will be fine? No incorrect drive paths and whatnot? I want to make **sure** that Windows will still boot.

[EDIT] Trying it anyway. If it doesn't work I'll get back on the LiveCD and seek more info.

---

### Post by BetaguyGZT on 2008-05-20
Well that didn't work. I'm pretty sure the system installed -- minus GRUB. it simply booted into WindowsXP.

Anyone have any ideas, short of me unplugging my storage drive?

---

