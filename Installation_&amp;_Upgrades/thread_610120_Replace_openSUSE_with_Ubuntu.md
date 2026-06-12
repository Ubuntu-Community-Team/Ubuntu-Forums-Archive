---
title: "Replace openSUSE with Ubuntu"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Socket370 on 2007-11-11
Hi,

6 months ago, I installed openSUSE on my laptop in a dual-boot configuration with Windows XP. In spite of much help, I've been unable to get WiFi, Sound or Printing to work in SUSE and thought I'd give Ubuntu a go.

SUSE installed something called Grub, which lets me select SUSE or Windows when I start, and I want to proceed carefully so that I don't make my PC unbootable by wiping out something I shouldn't.

In addition to the NTFS partition with Windows, there is a FAT32 partition with the Windows restore files, but since installing SUSE, it hasn't shown up any longer when I boot. I'm not too worried about this because I also have the Windows restore CD if I need it.

There is an extended partition on my system containing a "linux-swap" drive (1.39 GB) and two EXT3 drives (11.23 and 17.58 GB). I assume this is where I want Ubuntu to go, except I'm not sure why I have two EXT3 drives (other than the fact that that's how SUSE configured itself).

Can someone step me through what I need to do to replace SUSE with Ubuntu, but maintain my ability to select either Windows XP or Linux on boot?

The PC is a Gateway MX3414 with AMD Turion 64 and I have the 64-bit version of Ubuntu 7.10 on a CD, which my machine can boot in to okay.

Thanks!

---

### Post by wjp.reg on 2007-11-11
I would suspect that SUSE set up separate partitions for / and /home and installed grub in the MBR of the hard  drive.  If SUSE is still running, you can check the layout SUSE used by inspecting the /etc/fstab file.

You can install 64/32-bit Ubuntu by manually specifying which partitions to use for / and /home and swap, and then formatting them accordingly.

---

### Post by Socket370 on 2007-11-13
> **wjp.reg said:**
> I would suspect that SUSE set up separate partitions for / and /home and installed grub in the MBR of the hard  drive.  If SUSE is still running, you can check the layout SUSE used by inspecting the /etc/fstab file.

You can install 64/32-bit Ubuntu by manually specifying which partitions to use for / and /home and swap, and then formatting them accordingly.

I believe this is correct. The default "automatic" install option seemed to suggest that Ubuntu only needs a Swap and 1 partition, not two. Does it need a / and a /home partition? If so, I can easily assign the existing partitions as you suggest because they are already there. Will the Ubuntu install wipe the SUSE files, or should I do that first?

Also, will Grub continue to function? My fear is doing something that will make my computer un-bootable.

Thanks!

---

### Post by wjp.reg on 2007-11-13
> **Socket370 said:**
> I believe this is correct. The default "automatic" install option seemed to suggest that Ubuntu only needs a Swap and 1 partition, not two. Does it need a / and a /home partition? If so, I can easily assign the existing partitions as you suggest because they are already there. Will the Ubuntu install wipe the SUSE files, or should I do that first?

Also, will Grub continue to function? My fear is doing something that will make my computer un-bootable.

Thanks!

Separate / and /home partitions are often recommended, for ease of upgrade purposes, but not necessary.  In your case you might wish to continue with that setup.

Ubuntu will reformat the partitions if you tell it to :-) and you should.

Grub will get reinstalled into the MBR unless you use the 'advance' button and tell it to do otherwise.

Good luck!!

---

### Post by Socket370 on 2007-11-18
> **wjp.reg said:**
> Separate / and /home partitions are often recommended, for ease of upgrade purposes, but not necessary.  In your case you might wish to continue with that setup.

Ubuntu will reformat the partitions if you tell it to :-) and you should.

Grub will get reinstalled into the MBR unless you use the 'advance' button and tell it to do otherwise.

Good luck!!

Thanks... the install went smoothly, Grub and all. I am having some difficulties with Ubuntu itself, but I'll post those in the appropriate area.

---

