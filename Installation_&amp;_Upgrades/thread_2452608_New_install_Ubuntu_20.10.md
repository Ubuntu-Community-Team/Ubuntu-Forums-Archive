---
title: "New install Ubuntu 20.10"
date: 2020-10-25
forum: Installation &amp; Upgrades
---

### Post by jerry47 on 2020-10-25
I have a question about a fresh install of 20.10. When booting off the install usb drive you have two choices. Legacy boot or UEFI. My Asus Z77 has issues with booting UEFI if I remove the SSD serial cables. Its a firmware problem. You can never boot off the disk again unless I format it. The machine is my test machine with 7 SSD's. Booting legacy has no problem switching drives and there are up to 7 Linux distros at any given time. Ubuntu 20.04 is one of them. It boots legacy MBR without issue. 

20.10 is different. It does not partition a new drive MBR only GPT. Legacy boot is solved by Ubuntu creating three partitions. A bios-boot to interface the legacy hardware, an EFI partition, and the root partition. The machine boots legacy but the disk is partitioned GPT. 

Does anyone know if MBR is going to be supported like 20.04 and previous versions or is this a bug? If one goes the manual partitioning it comes up with a warning about the bios-boot partition not being present. Sometimes it does configure the disk MBR. It boots but will not load. Sometimes it configures the disk GPT. There's no selection for the user.

---

### Post by Dennis N on 2020-10-25
Format it yourself to MS-Dos partition table and create the partitions you need beforehand. You can do this from the live media. Then start the installer and use the 'Something Else' option for Installation Type;  select root partition with requested details, and install.

---

### Post by oldfred on 2020-10-25
In UEFI, if you remove a drive, it forgets the UEFI boot entry.
You have to manually add it back in with efibootmgr.

If external drives, you need an ESP on every drive, so UEFI can boot /EFI/Boot/bootx64.efi. That is UEFI boot for external devices.

Do you have latest UEFI for your motherboard.
I have newer Asus z97 and if I use too many drives & try to boot, I have similar issue. Once in a while I have to unplug everything, boot a USB flash drive and then install one drive at a time adding boot entries. Then I am ok for a while. Have had to houseclean UEFI entries and once just reinstalled same version of UEFI to clean it up.
So Asus does seem to have some UEFI issues, but I do not think it is MBR(msdos) vs. gpt issue.

But I also have used gpt with BIOS boot and the bios_grub partition on even older systems without issues.

---

### Post by jerry47 on 2020-10-26
Boards too old. No more firmware updates for the UEFI. I don't think its a MBR or GPT issue either. My question mostly was why there's no option for MBR partitioning on the installer. It just comes up with a warning that you have manually configured it wrong. I just want to know if this was done on purpose or its a bug.

---

### Post by jerry47 on 2020-10-26
I have used gparted to configure it myself. Most of the time the first thing the installer does is convert it to GPT when you hit continue. Then because I have not configured the bios-boot, EFI, and root partitions it comes up with a warning that it may not boot. Which is true. If I persist on changing it back to MBR it sometimes will leave it alone but sends the warning that it won't boot. Which is not true. It boots then gets stuck. I did find a bug report about an MBR issue but not sure if its referring to this problem or not. I would think if one chooses to let Ubuntu configure it, that it would default to the bios-boot option which is exactly what it does and its running now. But if one wants to insist on MBR then it should allow the user to just configure it root and default to MBR not GPT.

---

### Post by jerry47 on 2020-10-27
Here's the bug report that may apply to the problem I found while trying to install using MBR rather than GPT. 

[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1891324](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1891324)

---

### Post by Dennis N on 2020-10-27
Since the 20.10 installer won't handle it properly - if I had to have a working 20.10 BIOS system on MS-DOS partitioned disk, I think I would do a minimal install using the 20.04 installer, update all the packages, then upgrade the 20.04 system to 20.10 with the software updater. That may work.

UPDATE: Tested in a VM; this idea does work.

---

### Post by jerry47 on 2020-10-28
Yes Dennis, I thought of that too. But my goal is to get the installer fixed. I assume that changing the installer to default GPT for legacy boot probably messed it up in the first place. I've got it on a disk and its booting GPT with bios-boot. The bios-boot partition does work very well so far. But this issue should be resolved by the developers. I tried Kubuntu as well no shock that it does the same thing. My daily driver is Ubuntu 20.04 on two machines (one being the Z77 test machine and the other an Intel NUC booting UEFI) and three monitors. Dual monitor is on the test machine. At this juncture I have Debian 10 (for its stability to host a Unifi controller), Linux Mint 20.04, Manjaro KDE 20, Manjaro Gnome 20, and Manjaro Cinnamon 20. Thanks for testing on the VM.

---

### Post by brennus on 2020-11-14
[FONT=arial][COLOR=#333333]It's amazing that users with MBR are simply unable to install 20.10. The only option is to install 20.04 and then upgrade. I can't understand how such an evident bug passed all the testing. Nobody uses MBR anymore?[/COLOR][/FONT]

---

### Post by oldfred on 2020-11-14
My 2006 BIOS only system is using gpt and has since about 12.04 without issue. It does not have the FAT32 ESP, but does have to have the bios_grub partition.
I have used gpt since about 2010 on all systems and larger flash drives. Since most systems are UEFI, they should only be gpt whether user currently wants BIOS or UEFI boot as then easy to convert boot mode. But if MBR, drive usually has to be erased to convert to gpt and use UEFI correctly. Some tools may convert in place but better to start with gpt on blank drive.

Ubuntu has let users install UEFI boot to MBR partitioned drives. And that usually is dual boot & breaks Windows.
So it should not be installing in UEFI mode to MBR drives.]
Not sure if installer does not know if booted UEFI or BIOS to know if gpt required or not?

---

