---
title: "Trouble installing ubuntu"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by maledikt on 2008-08-06
Hi :confused:

I'm new and trying to learn how to use Ubuntu. I've downloaded both i386 and the amd64 versions and written both to CDs. My hard drive has 2 partitions, one NTFS and one ext3. Whenever I load either CD and go for the install I get stuck on the "Select Partition" as there is nothing there to select. It seems the installer doesn't detect my hard drive or something.
I've tried going to the terminal and writing "fdrive  -l" and "sudo fdrive -l" but nothing happens. (I get no info either, just drops to the next line.)

I am currently trying to run a dual boot, one Windows XP and one Linux Ubuntu. I'd really appreciated if someone could guide me through the process as I really want to use Ubuntu over other distros, but if all fails I'm willing to try Fedora aswell.

P.S. I've tried using Gparted, but it detects no drive aswell. I have a Western Digital 320gb hard drive.

Cheers,
Maledikt.

---

### Post by dileepm on 2008-08-07
When the installer prompts for to "Select Partition" select manual partitioning may be it happens if there is error in error in partitions and reading them... It is recomended tohave a unallocated space before and then create a swap space and a ext2 or ext3 partition...

---

### Post by maledikt on 2008-08-08
I tried with unallocated, doesn't work either. And the installer doesn't prompt me if I want to do it manually or not. Maybe Ubuntu doesn't support the Western Digital harddrives?

---

