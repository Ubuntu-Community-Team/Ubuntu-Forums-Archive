---
title: "Win 7 grub option missing after installing Ubuntu 14.04/16.04"
date: 2016-12-25
forum: MINT
---

### Post by tim-spargo on 2016-12-25
Hi,

I dual-boot all my computers with Ubuntu and WinX, but I run Ubuntu almost all the time.

Some time ago, on a new PC with only Win7 installed, I installed Ubuntu 14.04 from the Live CD. I chose to configure the installer to install Unbuntu alongside Win7. Unfortunately once I rebooted didn't have an option to run Win7, only Ubuntu. This past summer I installed Ubuntu 16.04 LTS over top of Ubuntu 14.04. I was hoping that a newer version of GRUB would fix the issue with the missing entry for Win7, but it did not.  That's why I'm here...

In the past couple days I've had a bit of time to try and fix this. I've tried numerous things including running Boot-Repair with the "purge" option selected, manually adding an entry with the "40_custom" file with various GRUB command (the entry appears, but I haven't been about to launch Windows, and I'm not very familiar with Grub). All to no avail.
[URL="http://paste2.org/xasbn56b"]
[/URL]I've uploaded my logs to Pastebin so if someone here could take a look and provide suggestions, that would be great.

[http://paste2.org/xasbn56b](http://paste2.org/xasbn56b)

Thanks for your interest.

---

### Post by oldfred on 2016-12-25
Moved to MINT sub-forum since not Ubuntu.

You have Windows & Mint installed in the 35 year old BIOS/MBR configuration.
It does look at one time you had Ubuntu in UEFI boot mode as it has a commented out entry to boot the ESP - efi system partition. Drive must have been gpt.

Windows only boots in UEFI mode from gpt. And if you install default Windows 7 from DVD it only installs in BIOS mode converting a gpt drive to MBR(msdos).  Windows 7 can be installed in UEFI mode from flash drive with minor modifications.

You need to boot installer & Boot-Repair in BIOS mode, or same mode as installs. But it looks like Boot-Repair did reinstall grub-pc which is for BIOS booting.

Configuration looks correct, but this may be a clue.
>  Windows not detected by os-prober on sda3. 


The Linux NTFS driver will not mount nor see NTFS partitions that are hibernated nor if it needs chkdsk. I might check if hibernated and run chkdsk to see if that is the issue. NTFS always needs chkdsk after a resize, so if originally resized with gparted that may be the issue.

If you do not have a Windows repair disk or installer with repair console you may have to temporarily reinstall a Windows boot loader and see if you can get into the Internal repair console. But you have boot flag on sda3, and it looks like sda2 may have been the Windows boot partition which has the internal repair console. You have all the necessary Windows boot files in sda3(Boot-Repair usually copies bootmgr & BCD from Windows boot partition into main partition as backup.

---

### Post by tim-spargo on 2016-12-26
Thanks oldfred. Of course you're right it is a Mint 18 install but since  it uses a Ubuntu base I thought it would be fine to post on the main  Ubuntu site and I didn't know about the Mint option. My bad... 

Thanks  for your detailed reply.
> 
If you do not have a Windows repair disk or installer with repair  console you may have to temporarily reinstall a Windows boot loader and  see if you can get into the Internal repair console.
In fact I do have the recovery DVDs for Windows.  I will give that a try and see if I can recovered Windows and if  successful, boot from a live Mint DVD and run boot-repair.

---

