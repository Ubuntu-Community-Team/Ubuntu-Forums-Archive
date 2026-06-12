---
title: "Which partition table type to use on fresh install"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by frostypepper on 2010-04-19
Using ubuntu minimal install 9.10 for a htpc. My boot drive is a 2Gb disk on module. When using advanced install I am eventually given the option to format the drive and ultimately the option to pick what sort of partition table type. I am not sure what to pick; it appears to have msdos as a default. Here are my options:

aix
amiga
bsd
dvh
gpt
mac
msdos (default?)
pc98
sun
loop

Some appear to be obviously bad choices; but I am not sure. Any ideas on which would be a better pick for me? I have already used msdos and it seems to work fine. Any input is welcome.

---

### Post by srs5694 on 2010-04-19
For a Linux-only system, either Master Boot Record (MBR; called "msdos" by most libparted-based tools) or GUID Partition Table (GPT) will work fine. MBR is more common, but GPT has some advantages, including support for larger disks (MBR tops out at 2TiB), partition names, no confusing or limiting primary/extended/logical partition distinctions, on-disk backups of partition table data, and CRC values to help spot corrupt partition tables. The biggest drawback to GPT is compatibility; not all OSes support it, and Windows in particular can't boot from GPT on BIOS-based computers (although Windows Vista and later, and some earlier versions, can read GPT data disks).

Overall, then, for a Linux-only system, or for a system that boots Linux and other GPT-friendly OSes (such as FreeBSD or Mac OS X), I'd go with GPT. If the system must dual-boot Windows, I'd go with MBR (except possibly on disks from which Windows doesn't boot, depending on the Windows version). If you go GPT, be sure to create a [BIOS Boot Partition,](http://grub.enbug.org/BIOS_Boot_Partition) which is a partition type that GRUB 2 uses on GPT disks to improve its reliability. To do this, create a small (~30KB-1MB) partition and set the bios_grub flag in parted or GParted or set the partition type code to EF02 in gdisk.

That said, if you pick MBR for a Linux-only system, it's not the end of the world. Linux has been using MBR for a long time; it's just that GPT is an improvement, and a modest one for most disks.

---

### Post by frostypepper on 2010-04-19
srs5694 thank you so very much; I had read up a bit on gpt but wasn't sure. You have answered a question that has been driving me nuts for a week. Hats off to you sir. Thanks again.

---

### Post by sofistik8d on 2010-08-14
I'm trying to create a new partition table on an external hard drive. I'm using Linux, Windows and Mac; I'm switching from Windows Vista to Mac OS X and need to move data from one to the other but I ran into some problems with the hard drive so I completely erased it. Hence, I need to create a new partition table and reformat the filesystem to NTFS in order to support all three.

Which should I choose? It sounds like GPT will allow my external HDD to be read by Vista, OS X and of course Linux (I'm on Ubuntu 10.04 Lucid Lynx).

---

### Post by srs5694 on 2010-08-23
sofistik8d, either GPT or MBR will work for you, since Windows Vista, OS X, and Linux all support both partition table types for data disks. If you expect to *ever* use the drive under Windows XP or earlier, or other OSes that might not support GPT (say, BeOS), then you should stick with MBR. If you're 100% positive you'll never use the disk with a non-GPT-aware OS, then I'd use GPT, because of its (admittedly small) advantages, such as its backup data structures and checksums to help the OS spot corrupted partition tables.

---

### Post by Softworn on 2011-06-06
> **srs5694 said:**
> *Partition Table Explanation*

Thank you so much for the thorough explanation. That was a 5 star post. I want to print it out and read it to my future children (srs). =D>

---

### Post by konsultor on 2011-06-18
My thanks also.  Got me over a hump in the install.

---

### Post by digisus on 2012-06-03
Great post srs5694, very helpful. Thanks!

---

