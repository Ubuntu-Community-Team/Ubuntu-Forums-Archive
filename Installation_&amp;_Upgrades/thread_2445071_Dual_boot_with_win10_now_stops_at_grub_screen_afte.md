---
title: "Dual boot with win10 now stops at grub screen after update"
date: 2020-06-08
forum: Installation &amp; Upgrades
---

### Post by smbunn on 2020-06-08
[COLOR=#242729][FONT=Arial]I never got the chance to dual boot my machine. I seem to have screwed up where grub lives. I have a FAT partition on the drive Ubuntu lives on with grub in there, and also a EFI partition on my Windows ard disk with a /efi/ubuntu folder. I get to the grub menu and when I use 'set', I see the prefix points to efi/boot, which is a third location. I tried setting it to (hd0,msdos1)/efi/ubuntu and rebooted but it immedialtly lost that change and failed. Typing 'set' again showed it had reverted to the wrong setting.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Here is my paste bin after trying boot-repair after I used a rescue CDROM[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][http://paste.ubuntu.com/p/GvMxR8ffZN/](http://paste.ubuntu.com/p/GvMxR8ffZN/)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How can I correct this please.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Simon[/FONT][/COLOR]

---

### Post by yancek on 2020-06-09
Partition "nvme0n1p2" is your windows EFI partition which contains the correct files to boot windows.  sda1 is an EFI partition on another drive which contains the Ubuntu EFI boot files.  I don't see a partition which has Ubuntu on it?  Generally, an Ubuntu install will put its EFI files on the windows EFI partition if it already exists but this is not necessary.  Your boot repair output does not contain a lot of information usually shown for whatever reason.  It doesn't look like Ubuntu was installed.  I would suggest that you read the Ubuntu documentation on dual booting UEFI with windows 10 at the link below to see if that helps.  Post back if you have additional questions.    

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-06-09
You have newer UEFI system.

But your drives are the old MBR(msdos).
Windows only boots in BIOS mode from MBR.
Windows only boots in UEFI mode from gpt partitioned drives.

How you boot install media is then how it installs for both Windows & Ubuntu. 

Better to back up all your data and reinstall both systems in UEFI boot mode.

---

