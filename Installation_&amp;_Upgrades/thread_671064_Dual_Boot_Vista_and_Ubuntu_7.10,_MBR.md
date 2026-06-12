---
title: "Dual Boot Vista and Ubuntu 7.10, MBR???"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Telescope_Nerd on 2008-01-18
Hi all
My shiney new laptop came with Vist pre-installed, and two 150GB hard disks. This seems like a lot of space to me. I have installed all the windows programs I need and this comes to 70G. Anyway I plan to Install Ubuntu 7.10 on the second (currently empty) drive and dual boot.

I have been doing a lot of reading of the forums to see If I can find some simple instructions for doing this. And there's loads of great advice! However there's just one bit which I need some more info on: the MBR.

There's a lot of discussion about conflicts between GRUB and vista's boot loader i.e. GRUB partially overwriting vista's bootloader and restoring vista's bootloader overwriting GRUB etc. Although my machine came with vista pre installed, no vista disks came with it. So I don't really want to play around with it untill I understand what's going on.

If anyone has any usefull information/advice/links that can help me understand this issue and get the bootloaders living together in harmony I would really appreciate it!

---

### Post by glennzo on 2008-01-18
Then the first thing to do would be to create a set of restore disks for Vista. Most systems have this option and it's often recommended to do that as soon as you can after purchase.

---

### Post by Telescope_Nerd on 2008-01-18
Great advice thanks, I'll do that for a start.

---

### Post by glennzo on 2008-01-18
Very welcome. I was lucky enough to get a restore DVD with my Toshiba laptop. When I hosed my system I used the DVD to get the system back to original condition. Worked well. Now I happily boot Fedora, Centos, Vista and XP with 1 160GB disk.

---

### Post by sandysandy on 2008-01-18
> **Telescope_Nerd said:**
> Hi all
My shiney new laptop came with Vist pre-installed, and two 150GB hard disks. This seems like a lot of space to me. I have installed all the windows programs I need and this comes to 70G. Anyway I plan to Install Ubuntu 7.10 on the second (currently empty) drive and dual boot.

I have been doing a lot of reading of the forums to see If I can find some simple instructions for doing this. And there's loads of great advice! However there's just one bit which I need some more info on: the MBR.

There's a lot of discussion about conflicts between GRUB and vista's boot loader i.e. GRUB partially overwriting vista's bootloader and restoring vista's bootloader overwriting GRUB etc. Although my machine came with vista pre installed, no vista disks came with it. So I don't really want to play around with it untill I understand what's going on.

If anyone has any usefull information/advice/links that can help me understand this issue and get the bootloaders living together in harmony I would really appreciate it!

u may consider backing up your mbr and then saving it on external media or some other partition. the backup would generally save in home folder.
code is
[COLOR="Blue"]sudo dd if=/dev/sda bs=446 count=1 of=backup-mbr18jan[/COLOR]

<sda may be replaced by actual drive identifier as required, eg sdb, hda>

for restoring the backed up MBR the code is
[COLOR="Blue"]sudo dd if=backup-mbr18jan bs=446 count=1 of=/dev/sda
[/COLOR]

specify the full pathname if backup is not in home folder.

regards

---

