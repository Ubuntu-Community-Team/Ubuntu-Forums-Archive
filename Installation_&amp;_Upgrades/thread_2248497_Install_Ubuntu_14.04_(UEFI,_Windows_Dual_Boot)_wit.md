---
title: "Install Ubuntu 14.04 (UEFI, Windows Dual Boot) with FakeRaid RAID0 active"
date: 2014-10-15
forum: Installation &amp; Upgrades
---

### Post by ambarry on 2014-10-15
Ok, I'm at the point of having to go back to Windows from Ubuntu for the first time in 9 years!!!  NOoooo!!!

Problem:  Laptop has SSD+HDD combo (32Gb + 750Gb) set up as a RAID0 to cache the HDD.

Minor problem: Its UEFI, SecureBoot etc.  But these aren't the problem ... all detected and dealt with Ok.

The problem is the FakeRaid.  The Ubuntu installer doesn't detect the RAID0 or any partitions and so simply suggests I install Ubuntu over all the existing OS.  Following all advice from many forums,  I run modprobe dm-mod; dmraid -ay beforehand.  The installer then sees the Partitions and using the manual allocation options I select the pre-prepared partitions for root, & Home (Swap and EFI are picked up Ok).  I select the RAID root for the boot partition (which I know is also correct).

The installer runs and all looks Ok.  The write to /EFI always leaves nothing ... it seems to be cached on the SSD and not written through to the /EFI partition, but I got around this by copying the files to USB and copying them back again afterwards.  I then change the UEFI menu to point to the GRUB entry (the OS complains if I try the shimx64 entry) and we're off.

But, we're not ... GRUB doesn't find Ubuntu to boot.  It seems the Ubuntu partition is not written properly either.  Caching again?  Probably not ... I suspect that dmraid just doesn't find all the information it needs to mount the RAID0 properly.

This one really has me stumped!!  Spent weeks on it now.  Even tried the Fedora installer, which uses mdadm, but (and I've tried mdadm in Ubuntu and it does the same) the mdadm finds the raid drives but doesn't find the partitions at all.

Basically, Ubuntu is uninstallable on this ultrabook set up.

I hardly use Windows - only for two programs that have no Linux equivalent.  But I do need it.

Any ideas?  [And PLEASE don't suggest I 'read the forums'.  I've spent two weeks on this already!].  I _am_ an expert user - lecturered Computer Science at a top 10 UK Uni for over 20 years.  Just need confident and definite pointers.

Thanks!!

Many thanks to anyone who can help.

---

### Post by oldfred on 2014-10-15
When you copy /efi/ubuntu to your efi partition, did you update the grub.cfg in the ubuntu efi folder?
It should just be a three line configfile entry to tell system to use grub.cfg in your install.

This is mine, but partition and UUID must match your install.

search.fs_uuid 45de38c8-6748-4634-b207-628d9aa8b42b root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

I have seen some with just one line. But search is intended to override incorrect device setting if partitions change by using UUID.
 configfile (hd0,gpt7)/boot/grub/grub.cfg

Not sure with RAID how it may be specified. /dev/mapper/something??

---

