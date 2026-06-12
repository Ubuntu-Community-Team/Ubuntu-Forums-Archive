---
title: "One way to get a bootable 16.04 server UEFI GPT disk image"
date: 2016-05-24
forum: Installation &amp; Upgrades
---

### Post by Jawfish on 2016-05-24
**Goal:** I needed to have a standard disk image that we can use on many endpoints. We'll use dd to install it and then expand the partitions to fit. It has to work on HDDs/SSDs/USBsticks.
[B]
Problem:[/B] I was unable to get a bootable UEFI disk using the 16.04 installer, even after following much advice from experts. Bootable MBR was easy.

Note: this recipe may not work with your BIOS. 

After many experiments I succeeded with this recipe:

**Set BIOS to UEFI only.** This changes the way the installer works. *This was the key breakthrough for me YMMV*.

**Option 1:**  you need a multi-partition, multi-boot setup.

[LIST]
[*]Using a 16.04 installation, ( might work on 14.04, but safer to use Xenial) run gparted ( or parted) 
[*]Insert your target drive or flashdrive, reboot as needed
[*]and 
[*]Make the target disk gpt
[*]create a Fat32 partition at the beginning of the disk, recommendations vary from 200-500Mb. 
[*]Make your other partitions as you wish, even if they are root they won't be bootable.
[*]The EFI partition must be bootable, and choose "EFI..." for its use
[*] You do not need to set the EFI partition to mount at /boot/efi, the installer took care of that
skip to installer instructions below
[/LIST]

I tried to create the partitions using the installer, and you might get that to work, but this recipe is what worked for me.

[B]
Option 2:[/B] you just need a single-boot system that works
skip to the installer below

installer instructions:
[LIST]
[*]Insert USB livecd stick  and reboot on the USB stick.
[*]Being careful not to change your pre-installed system ( the installer will try to use other efi boot partitions and swap spaces, if they are available, for instance on your installed system)
[*]Run the installer as usual and choose guided or manual partitioning. I found that with 4 installed partitions I could use guided and still get what I want, but be sure to check the plan before you say "yes" write to disk.
[*]
[/LIST]

Notes:
By "installer" I mean the server 64 bit iso copied to a flashdrive. It may be that 32bit versions do not handly UEFI/GPT well, esp grub.
Get a fast flashdrive, don't waste time on cheapies.
If you need a second boot partition, I was able to simply copy the files for the installed partition to the second one, edit fstab and the grub files with the correct UUIDs and hd#-part# in the menus, run update-grub and get it working.

---

### Post by sudodus on 2016-05-24
Your approach is not too different from mine:

[ Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

It is a good idea to share the methods :-)

---

