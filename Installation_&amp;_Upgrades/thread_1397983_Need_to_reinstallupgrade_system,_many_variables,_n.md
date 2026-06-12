---
title: "Need to reinstall/upgrade system, many variables, need advice on how"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by Cyber Akuma on 2010-02-03
Ok, I have a laptop that is currently partitioned like this, I have been meaning to upgrade it for a long time and haven't used it in a while:

NTFS Vista
exf4 Ubuntu
exf3 OpenSUSE
Swap (For Ubuntu)
Swap (For OpenSUSE)

The bootloader is grub1.

I plan to wipe (but not delete) the NTFS partition and install Windows 7 in it's place. (Its an upgrade edition, but once the upgrade installer has determined that I have a legit install of Vista I will tell it to just reformat the NTFS partition instead of migrate the data).

I also want to update (through the updater, not a cd/dvd) Ubuntu to the latest version of 9.10 (I think its at 9.04 currently). Main reason being I spent a lot of time with the package managers getting the software I want and do not want to have to go through all that again.

And finally, I also plan to reformat the ext3 partition to ext4 and reinstall OpenSUSE (from cd/dvd).

But I am not sure how to go about this, I want basically the end result to be my bootloader being grub2 and the grub2 files to load from the Ubuntu partition, but for the bootloader to support windows and opensuse without having to manually update the file every time OpenSUSE has a kernel update (if that is possible). I want grub2 to have options to boot Windows7 (NTFS) Ubuntu (ext4) and OpenSUSE (ext4).

In what order would you recommend I install/update everything?

How would you recommend I go about doing all this?

Thanks

---

