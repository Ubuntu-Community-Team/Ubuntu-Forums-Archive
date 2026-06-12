---
title: "GRUB Error 15..Can't remember how to fix it"
date: 2017-10-29
forum: Installation &amp; Upgrades
---

### Post by sports fan Matt on 2017-10-29
It's been a long while sine I dabbled in Ubuntu, and I have a spare laptop that ran it well before.  Was going to put 17.10 on it, but since it's been a year or so since I dabbled in Linux, I can't remember how to get it to boot.

I was going to try 9.10, (last CD I had) and at least get into the live cd and then upgrade.) Yes a long while and yes several upgrades, but a bootable CD isn't an option for a bit.  Would it be better to order a 17.10 disc /repair grub or..

---

### Post by oldfred on 2017-10-29
Grub2 does not use errors, that is from grub (now grub legacy).
[https://www.gnu.org/software/grub/manual/legacy/grub.html#Troubleshooting](https://www.gnu.org/software/grub/manual/legacy/grub.html#Troubleshooting)

But better just to install 16.04, you can download from here, but if an older system, you may need or want a lighter weight system.
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements. Regular Ubuntu does not fit on CD anymore, requires DVD or flash drive.
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) 

Lightweight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by sports fan Matt on 2017-10-29
Hi Fred,

I can do that.  This is an I5 core processor so I have more then enough adequate space.

---

### Post by sports fan Matt on 2017-10-29
Quick update.  Found a 12.04 Precise disk so was able to boot off the hard disk of it.  Insalling Tahr next then up to 17.10.

---

### Post by oldfred on 2017-10-29
If an i5 CPU, then it is a newer computer with UEFI.
And then better to partition with gpt, unless you also are installing Windows in BIOS boot mode.

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

