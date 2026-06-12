---
title: "NTLDR is missing after reinstalling windows"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by psynaps3 on 2007-01-27
Hi,

I am having some trouble after reinstalling windows on my dual boot system (windows/edgy). 

The partition table looks as follows,
P1 - (P) 100mb - Dell Diagnostic partition - FAT16
P2 - (P) 35gb - Windows XP - NTFS
P3 - (P) 128mb - Boot (Linux) - EXT3
P4 - (E) Remaining space
P5 - (L) 1gb - Swap (Linux) - SWAP
P6 - (L) 20gb - Root - EXT3
P7 - (L) 15gb - Home - EXT3

After I reinstalled XP, I rebooted using a live cd and set the boot flag to P3 (where grub is). However, now Windows works only if I set the entry in menu.1st to hd(0,0) and even in this case, the Dell diagnostic partition shows up as the C drive in windows! How I can fix this issue? 
I am assuming that the correct behaviour should be hd(0,1) in the menu.1st and the primary windows partition showing up as the C drive instead of the Dell diagnostic partition.

In C drive, i can find NTLDR, NTDETECT.COM and certain other windows related files. Would simply copying these file (which all?) to the root of the windows installation and setting the menu.1st appropriately do the trick? Further on, how can I remap the drive letters in Windows?

Many thanks.

---

