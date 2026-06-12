---
title: "Ubuntu Gusty on ATA hd can't install properly if there's any partitions"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by infinideas on 2008-01-22
Hi everyone, I've been battling with my computer for more than 12hrs now and really need some help.

I'm trying to install Ubuntu Gusty on a ATA 160GB hd (was having a ATA 80gb older hd there, but just to eliminate any more problems/possibilities, I have it unpluged for now). Have been using the Live CD or Alternate CD to install, but both methods result in the Grub bootloader aren't able to install, when there's any partitions on the hd.

Before I try to install Gusty on this computer, I've just recently installed Gusty with the same Live CD on two brand new PC with single SATA hd. I normally first go to GPart and setup a "/" partition, a "swap" partition and a couple of "ftns" partitions for later windowsXP installation and my data files.

So that's what I did similarly on this older computer of mine, i boot into Live CD, do the partitions (same kind of setup, except having separate partitions for "/" and "/home"), and Grub just failed to install, plus after the installation it just goes back to the desktop and doesn't ask me to reboot like any normally successful ubuntu installations. I tried to use the Alternate CD and it fails to install Grub everytime. In the Live CD situation, even if I reboot it manually after the installation, it just fail to boot into Ubuntu.

I have try to search for an answer from the web/forum but no solutions yet. I tried to install Grub on floppy, or using Alternate CD's rescue mode (even worst as it doesn't even offer me the opinion to "re-install Grub"!) and none is working.

THE ONLY WORKING WAY so far, is to have a blank hd, without any partitions, and allows Ubuntu to install in guided mode during the partition stage. It doesn't even work if there's just a partition for /, /home and swap + the rest in free spaces!!! But I really don't want Ubuntu to take up the whole hd in guided mode partitioning as I want /home to separate and have some extra partitions in NTFS so my winXP can read its content.

If anyone know how to fix this, pls help. Would really appreicate! Cheers!

(p.s. don't know why I wasn't able to see myself the ntfs option in the GPart before, so i've been doing all the extra partitions in fat32. but that still doesn't explain the weird result even if there's just the /, /home and swap partitions and still failed. But I'll try again with ntfs for extra partitions just to see if it matters)

---

### Post by infinideas on 2008-01-22
Hi everyone, it's a bit embarrassing, but I've managed to find out why my Gusty installation has been a bit weird and not installing properly.

Apparently, I didn't had enough space on my "/" partition for the installation that's why it quite itself at around 70%!!! For someone who's been installing OSs and Apps frequently in the last 10+ yrs, that's so embarrassing! But that's due to my friend who advised me to separate / and /home, said i just need 2gb for / and i didn't noticed after GPart that 2gb became 1.9gb. And since I never just sat there and staring every % of the installation progress, I didn't know until the last installation try that Ubuntu in fact fired a warning saying /target partition is full and quit there back to desktop, so everytime I look at the installation progress at the end, I just don't find the proper installation completed reboot prompt.

Anyway, now that the reason has been found, Ubuntu Gusty has been successfully installed on my 2 hds-plugged-in-PC with all the partitions I wanted to have there.

Thanks for anyone who's trying to help !

---

