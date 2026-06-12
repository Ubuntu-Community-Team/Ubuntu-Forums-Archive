---
title: "Multiple Ubunus"
date: 2005-03-25
forum: Installation &amp; Upgrades
---

### Post by billjw on 2005-03-25
Hi all

I had a search but couldn't find anything on this so just direct me if this is answered somewhere else.

I reconfigured my HD to have Windows/Hoary/Spare partitions, so I could eventually install Linspire.

I ended up using the spare for Warty. GRUB show all distros on boot but can't boot into Hoary anymore ... I can select it but it just hangs.

Warty works and Windows works. I have info on Hoary I need so it's kinda important I get access to it.

Thoughts? Have I missed something obvious?

Bill

p.s. I'll reboot into Hoary now and write down the error message I get.

Here you go:
NTFS-fs error (device hda3): read_ntfs_boot_sector(): primary boot sector is invalid
NTFS-fs error (device hda3): mount option errors=recover not used. Aborting without trying to recover
NTFS-fs error (device hda3): NTFS_error ntfs_fill_sync(): not an NTFS volume
cramfs: wrong magic
pivot_root: no such file or directory
sbin/init  ;428 ; cannot open dev/console: no such file
Kernel panic - not syncing. Attempting to kill init

Hope that makes sense to someone.
It looks like it is reading hda3 as an NTFS file but it isn't and it didn't load that way.

---

### Post by Slavakion on 2005-03-25
[QUOTE=billjw]Hope that makes sense to someone.
It looks like it is reading hda3 as an NTFS file but it isn't and it didn't load that way.[/QUOTE]
Check to make sure grub isn't trying to mount it as a Windows partition. Failing that, I found this on another forum

> you are using a 2.6 kernel .. if no you can ignore the rest. and I'm wrong

starting at 2.6.1 there was a problem where when formatting a fat32 in windows ..MS woudl label the partition as a fat16 and teh 2.6 kernel will reject it.. if you format it in linux it shoudl fix the problem and also work in windows.. the truth is fat16 adn fat 32 work liek ext2 and ext3 there the same root. so if XP miss marks the partition type XP cares not.. but linux sees the two as different.. and will give you the error.
Might work. :/

---

