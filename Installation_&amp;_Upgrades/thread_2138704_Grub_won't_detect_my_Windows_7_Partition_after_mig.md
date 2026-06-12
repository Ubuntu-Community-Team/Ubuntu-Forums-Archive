---
title: "Grub won't detect my Windows 7 Partition after migrating from HDD to SSD."
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by clungzta on 2013-04-25
Hi,
Ive been Dual-Booting Ubuntu 12.04 and Windows 8 for a few months now, I now use Ubuntu 90% of the time but I still need Windows for some unsupported Linux software.

I am fed up with the new Windows 8 GUI and am now reverting back to Windows 7 while upgrading to the SSD.

I did a clean DVD install of both Windows 7 and Ubuntu 12.04 on my SSD, while leaving the Windows 8 Partition as is,  to transfer across important files.

Ive set Grub as the default bootloader, it detects my Windows 8 and Ubuntu partition's but not Windows 7. Any Ideas?


This is how my partitions are set up according to GParted:

[TABLE="width: 500"]
[TR]
[TD][SIZE=1]Partiton
[/SIZE][/TD]
[TD][SIZE=1]File System
[/SIZE][/TD]
[TD][SIZE=1]Mount Point
[/SIZE][/TD]
[TD][SIZE=1]Label
[/SIZE][/TD]
[TD][SIZE=1]Size
[/SIZE][/TD]
[TD][SIZE=1]What it Is
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sda1
[/SIZE][/TD]
[TD][SIZE=1]ntfs
[/SIZE][/TD]
[TD][SIZE=1]/media/System
[/SIZE][/TD]
[TD][SIZE=1]System
[/SIZE][/TD]
[TD][SIZE=1]469.03GB
[/SIZE][/TD]
[TD][SIZE=1]Windows 8 Partition
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sda4
[/SIZE][/TD]
[TD][SIZE=1]ext4
[/SIZE][/TD]
[TD][SIZE=1]/home
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]30.97GB
[/SIZE][/TD]
[TD][SIZE=1]Ubuntu Home Directory
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sda2
[/SIZE][/TD]
[TD][SIZE=1]ntfs
[/SIZE][/TD]
[TD][SIZE=1]/media/Documents
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]1.32TB
[/SIZE][/TD]
[TD][SIZE=1]Windows Documents
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sda3
[/SIZE][/TD]
[TD][SIZE=1]ntfs
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]System _Recovery
[/SIZE][/TD]
[TD][SIZE=1]8.01G[SIZE=1]B[/SIZE]
[/SIZE][/TD]
[TD][SIZE=1][SIZE=1]System R[SIZE=1]ecovery tool[SIZE=1]s[/SIZE][/SIZE][/SIZE]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sdb1
[/SIZE][/TD]
[TD][SIZE=1]ext4
[/SIZE][/TD]
[TD][SIZE=1]/
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]13.97[SIZE=1]GB[/SIZE]
[/SIZE][/TD]
[TD][SIZE=1]Ubuntu Roo[SIZE=1]t[/SIZE]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sdb2
[/SIZE][/TD]
[TD][SIZE=1]extended
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]105.27GB
[/SIZE][/TD]
[TD][SIZE=1]?[SIZE=1] [SIZE=1]I didn't assign this.[/SIZE][/SIZE]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sdb5
[/SIZE][/TD]
[TD][SIZE=1]linux-swap
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]953.0[SIZE=1]M[/SIZE]B
[/SIZE][/TD]
[TD][SIZE=1][SIZE=1]Ubuntu Swap Partition[/SIZE]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sdb6
[/SIZE][/TD]
[TD][SIZE=1]ntfs
[/SIZE][/TD]
[TD][SIZE=1]/[SIZE=1]media/SSD[/SIZE]
[/SIZE][/TD]
[TD][SIZE=1]SSD
[/SIZE][/TD]
[TD][SIZE=1]104.34GB
[/SIZE][/TD]
[TD][SIZE=1]Windows 7 Partition
[/SIZE][/TD]
[/TR]
[/TABLE]

---

### Post by carl4926 on 2013-04-25
Is sda a GPT partition table
If so you need a bios_grub partition on sda if sda is to be the boot disk

---

### Post by clungzta on 2013-04-25
I only want sdb to be the boot disk, After i've salvaged all the old documents from Win 8 (/dev/sda1) I will be formatting and only using sdb (Ubuntu and Win 7) to boot.

---

### Post by carl4926 on 2013-04-25
Then you need to enter the BIOS and change the HD boot order
If Ubuntu is a New install it may be easier to then install it again over the top of what you have. But try it without re-installing first. It's just that it may not like sdb becoming sda
I see you have / and /home on different HD's? So re-install will help all round when you assign the mount points in the advanced setup

---

### Post by clungzta on 2013-04-25
I have always had sdb as the default in the BIOS, I put my home directory on sda because when I remove Windows 8, I want all documents on HDD and operating systems on SSD for a quick boot. I might aswell just give it a clean Install and see how it goes. 

Cheers.

---

### Post by carl4926 on 2013-04-25
If you ever pull a SATA or power from a HD it can change the boot order - FYI
Double check because if sdb is first it should be sda in fdisk or parted

---

### Post by Mark Phelps on 2013-04-25
> **clungzta said:**
>  ...I am fed up with the new Windows 8 GUI and am now reverting back to Windows 7 while upgrading to the SSD.

I don't like the Win8 GUI either -- which is why I installed the $5 Start8 app from Stardock --which gives me back the Win7 GUI complete with the old Start Menu and Win7-like desktop.  Since you PAID for Win8, you might want to look at this option before you throw it away.

---

### Post by darkod on 2013-04-25
Have you tried selecting Win8 from the grub menu? Does it show then option for 7 and 8?

Windows will combine boot files if you have more than one version installed. So, by adding win7 without taking other steps first, you might have made it combine the boot files with the win8 files. In that case grub2 can see only one set of files, and will create one entry in the boot menu.

But that entry should give you options for both windows versions.

---

### Post by oldfred on 2013-04-25
If your new install of Windows combined boot files & BCD into the Windows 8 install, you may be able to repair (add boot files) to your Windows 7 install.

May be best to see what is where. Boot-Repair will not fix most Windows boot issues. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

