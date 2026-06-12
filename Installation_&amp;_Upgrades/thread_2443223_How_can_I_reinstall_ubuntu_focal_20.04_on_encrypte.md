---
title: "How can I reinstall ubuntu focal 20.04 on encrypted system?"
date: 2020-05-12
forum: Installation &amp; Upgrades
---

### Post by liquidcarbon on 2020-05-12
Hi,
    I'm a very long time ubuntu user (over a decade) but have not been on these forums in a while as I've had no issues with Ubuntu. With the arrival of 20.04 LTS I decided to encrypt my data (or system if needed). I'm looking for the following:
- Method to reinstall ubuntu with LUKS encryption on a previous LUKS encrypted ubuntu install on a dual boot system with Win10.
- Keep all my personal files (ie /home folder) intact, with or without a separate partition. I do not wish to move everything out, reinstall and then move stuff back in.
- Simple GUI based approach through the standard installer. I know how to use the command line but I'd rather not, especially for something as sensitive as encryption.

    What I'm looking for is basically the same as this document: ([https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)) except that I need it on an LUKS encrypted system/partition. I tried doing this on a spare system with 20.04, and I could not find a way of telling the installer the passphrase to the encrypted system. The end result was a reinstall that wouldn't boot or the encrypted partition gets wiped out. I also tried to run installer with and without pre-unlocking the encrypted partition.
    I am able to do all of the above with Fedora,OpenSUSE,Manjaro, (although they only do this when /home is on separate partition, which is fine for me) so I'm not sure what I'm doing wrong in Ubuntu.
Thanks!

---

### Post by liquidcarbon on 2020-05-14
Based on the my personal experiments using the Ubuntu 20.04 installer, online research, and asking various forums (and lack of answers there), I conclude that as of today, there is no way to do all of the following:
- Installing/reinstalling Ubuntu ...
- using the installer GUI ...
- on a pre-encrypted system (LUKS, with separate /home partition or not) without destroying pre-existing personal files...
- with dual booting another OS.

Of course there are ways of doing this if you rely on the command line, which I was looking to avoid. I've decided to switch to Fedora 32 as it meets all these requirements. Ubuntu served me rather well for over a decade, hope to return when the above issue is fixed.

---

### Post by liquidcarbon on 2020-05-31
Bump

---

### Post by oldfred on 2020-05-31
I do not know nor use LVM.
But with encryption you absolutely must have good backups.

[https://help.ubuntu.com/community/ManualFullSystemEncryption/](https://help.ubuntu.com/community/ManualFullSystemEncryption/)
Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) & 
[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

---

### Post by liquidcarbon on 2020-05-31
Oldfred, Yes I totally agree. I run automated offsite backups on all my personal files every night, and local backups every few months. 

But I find the lack of support for advanced partitioning with encryption in the year 2020 quite surprising. An unencrypted personal laptop being  lost/stolen could easily turn into a financial disaster via identity theft/fraud.

---

