---
title: "Installation crash corrupts MFT, help!"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by marcus.nl on 2006-06-20
Hi,

I need help fixing my master file table on a data disk containing some music etc. I did not backup before... there is a solution out there since I had a similar problem years ago, but can't remember how I fixed it.

Story:
Couple of days ago I tried to install Kubuntu. Everything went fine until setting up the partitions and installing the boot loader. Then it crashed and after rebooting (no GRUB came up) I saw that all my data on my fat32 data partition was gone. 
Well it wasn't gone precisely since the disk info says of 40gb only 8gb are free but all former directories only came up as files (without anything in them, just like for example 'Downloads' or 'Temp'). 

I had a similar crash years ago: a friend pointed me at a command line tool (for win98) able to fix my master file table. It wrote the MFT new and all files showed up after repairing it. But I can't remember the name of the tool. 

So please help me to repair my disk so I can rescue some of my files and then try my luck with a new install, reformatting the hard disk completely!
(I'm able to recover some files by using EasyRecovery but 1000s of MP3s are not easily distinguished by file name only. Also the recovery does not work for openoffice files or other more rare formats.)

Here is the setup of my 60gb harddisk before installing:
primary: 5gb XP (fat32)
extended: 
40gb data (fat32)
5gb to be used for ubuntu -> format xfs
5gb to be used for suse -> format xfs (wanted to reinstall that anyway)
1gb /home -> format xfs
1gb /swap

Before installing Kubuntu I wrote repaired the master boot record with the winXP-CD repair console to get rid of a previous SUSE grub installation.

Any idea how to fix my partition problem is very welcome and I'll be very thankful if my problem can be solved.
Cheers,
Marcus

---

