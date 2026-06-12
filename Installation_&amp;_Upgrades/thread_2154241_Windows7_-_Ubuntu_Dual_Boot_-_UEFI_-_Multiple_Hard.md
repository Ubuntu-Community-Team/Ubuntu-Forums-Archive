---
title: "Windows7 - Ubuntu Dual Boot - UEFI - Multiple Hard Drives Question"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by xExekut3x on 2013-06-14
I have Windows 7 installed on one SSD. I want to install Ubuntu on another SSD, along with several other flavors. I have a UEFI BIOS. I've tried installing Ubuntu in legacy mode, but the SSD I installed it on doesn't show up in BIOS. I tried installing Ubuntu in EFI mode, I created an EFI partition (not really sure why or if it helped), and the SSD showed up in BIOS and I was able to boot from it, but I wasn't able to boot into Windows. How should I go about doing this? I want to keep the Windows MBR intact and install grub on the SSD I'll be installing Ubuntu on and let grub handle Windows. During Ubuntu's partitioning portion, there's an option for an EFI partition, or in legacy mode a BIOS partition. Do I need this? If so, how large should it be? Which should I choose? Should I install Ubuntu in EFI mode or legacy? This new EFI BIOS has got my head spinnin'!

---

### Post by oldfred on 2013-06-14
However you have installed Windows - UEFI or BIOS is how you should install all other systems to easily dual boot. UEFI & BIOS write hardware info to drive for system to boot from and do it differently. So the only way to dual boot with one UEFI and the other BIOS is go go into UEFI/BIOS and turn on or off BIOS boot mode. If both are the same mode then you can dual boot from grub menu.

With Ubuntu you can boot from gpt partitioned drives with either BIOS mode or UEFI mode. So may be best to configure any drive that would only be Ubuntu to be gpt and include an efi partition even if booting in BIOS mode. Then you could convert to UEFI later. It would be difficult to add an efi partition later as it needs to be first per UEFI spec although Windows usually makes it second after its own recovery/repair partition.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace

[/URL] I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by xExekut3x on 2013-06-14
Thanks for the reply. That helped out a lot. At the moment, I'm booted up in EFI mode on an Ubuntu Live USB. I've verified that my SSD is GPT, so I've created this partition scheme:
250 MiB FAT32 EFI Partition
1 GiB Boot Partition
32 GiB Swap Partition - I have 32GB of RAM and I do plan on using hibernation
30 GiB Ubuntu /root Partition
15 GiB Kubuntu /root Partition
15 GiB Mint /root Partition
~26 GiB excess Data Partition

The Ubuntu Installation screen is at the "Type" screen, my device path is /dev/sdf, with /dev/sdf1 being the EFI partition, and /dev/sdf2 being the boot partition. Do I point Grub to /dev/sdf or the /dev/sdf1 EFI partition?

---

### Post by xExekut3x on 2013-06-14
Well, it would appear I need to use BIOS, not UEFI. I went into my UEFI/BIOS and changed the boot options to UEFI Only, rebooted, and Windows wouldn't boot up. I went back in and changed it to Legacy Only, and Windows booted up. It would appear I don't need to use UEFI. So I guess I'll boot back into the Live USB in legacy mode and setup my partition scheme for BIOS, install Ubuntu, and see what happens.

---

### Post by xExekut3x on 2013-06-14
Fixed. I changed the partition style to MSDOS and everything works now, even EasyBCD. So many issues just because of GPT.

---

### Post by oldfred on 2013-06-14
I am sure it would have worked with gpt as that is what I use, but I only have BIOS so that avoids some of the issues. With gpt you have to have the 1MB unformatted bios_grub partition to get grub to install to MBR correctly for BIOS booting.

---

