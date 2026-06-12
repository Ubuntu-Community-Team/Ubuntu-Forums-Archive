---
title: "problems with EFI on asus ux32v"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by obsidianop on 2012-09-11
Hi,

I got a new Asus zenbook with the 24GB SSD and 500GB drive.   I thought I'd be clever and preserve the out-of-the-box windows installation on the 500GB and install ubuntu on the 24GB drive.   I got all of the partitions sorted out and ubuntu installed without any major problems, except I couldn't boot it - the bios (or UEFI "setup utility" I guess, now) just pointed to the windows bootloader and that's all I would get.  

So I ran boot-repair and asked it to set everything up for me - it knew about the two OSs and such ( [http://paste.ubuntu.com/1198790/](http://paste.ubuntu.com/1198790/) ).  After this, even the windows boot didn't work anymore.  Here's what I don't get:   Boot-repair tells me there are a couple of available boot files:

    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/boot.efi                         /efi/ubuntu/grubia32.efi

But when I go to the setup and enter these in the format specified

"add new boot option"
fs0:\efi\ubuntu\grubia32.efi

or 
fs0:\efi\Boot\bootx64.efi

neither one works! (the format is suggested by the setup utility) It just goes back into the setup utility when you try to boot.

Has anyone seen anything like this?  It just seems so simple: point it to an EFI file and go.
But apparently not, and until I figure it out I have a $1200 brick.

---

### Post by oldfred on 2012-09-11
Welcome to the forums.

Post BootInfo link from Boot-Repair.

With the new UEFI it can be efi boot or the older BIOS boot. Windows only boots in UEFI if drive is partitioned gpt. Ubuntu will boot from gpt in BIOS or UEFI modes. And both boot from BIOS with MBR partitions.

Often the main issue is that both systems must be installed in UEFI mode or both installed in BIOS mode.

From BootInfo report we can see how systems are installed and make suggestions on which way to go.

In case others find this thread and do not have link to Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

These were Dells with Intel Smart Respose.  That somehow used RAID which had to be removed.
 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

We also have seen SSD just used for hiberfil for Windows without RAID settings. Then hiberfil should be recreated in the Windows install.

---

### Post by YannBuntu on 2012-09-11
Hello

> **obsidianop said:**
> [http://paste.ubuntu.com/1198790/](http://paste.ubuntu.com/1198790/)

1) You can restore the Windows EFI backups by running Boot-Repair -> click "Advanced options" -> untick "Reinstall GRUB", tick "Restore EFI backups" -> click "Apply".

2) I see 2 possible mistakes: you have installed Ubuntu32bits (EFI may be better supported in 64bits), and you have placed the Ubuntu partition on the other disk. If I were you, I would delete (via Gparted) the sda6 and sd**b**1 partitions (this will freed 21GB on the 500GB disk), then disconnect the 24GB disk (if possible), then install Ubuntu64bits (or better: [Ubuntu-Secure-64bits]("http://sourceforge.net/projects/ubuntu-secured/files/ubuntu-secure-remix-12.04.1-64bits.iso/download"), as it comes with pre-installed Boot-Repair) in the 500GB disk.

---

### Post by obsidianop on 2012-09-12
Hi, thanks for your help!

>  you have placed the Ubuntu partition on the other disk

Yes, I realized this might make it a little harder, but I thought the small disk might be nice because it's SSD so I figured it would make for faster boot times and such.   If nothing else works I will give up on that.  

I will try the 64-bit first though!

---

### Post by xanderp123 on 2012-10-09
Hi obsidianop,

I have an Asus UX32V and I was thinking about installing Ubuntu to the 24 GB SSD as well. Did you get everything working?

---

