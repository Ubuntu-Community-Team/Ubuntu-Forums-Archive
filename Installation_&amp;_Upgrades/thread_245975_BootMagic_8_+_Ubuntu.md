---
title: "BootMagic 8 + Ubuntu"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by Cavecat on 2006-08-28
Hello,

I found this  thru Google  :
[http://www.linuxforums.org/forum/red...-core-4-a.html](http://www.linuxforums.org/forum/red...-core-4-a.html)

I'm more or less trying to do the same thing but I have this setup :
Nvidia Nforce4 with 4 SATA discs (no RAID)
- SATA 1 : 160 Gb , contains 3 Partitions
1 :Primary NTFS , XP Pro
2 :Primary NTFS , Vista (forced into XP bootloadermode)
3 :Logical NTFS
-SATA 2 : 160 Gb 
1 : Logical NTFS : contains data , accessible from XP&Vista (Pictures,..)
-SATA 3 : 80 Gb
1 : Ext3 for Ubuntu 
2 : Linux Swap
-SATA 4 : 80 Gb
Empty , perhaps Gentoo later (looking to learn about Linux)

Now , I'm using BootMagic 8 since I want to separate my operating systems as much as possible , I really want to be able to kill one of them without tampering with the other ones.
Since XP is my 'primary' OS , I like BootMagic because I can start it from there. I've good experiences with it but support is non-existant now it has been bought by Symantec.

What I did :
- Download Dapper Drake Alternate AMD64 CD
- Installed Ubuntu to /DEV/SDC (as you can read above)
- Installed GRUB onto /DEV/SDC1

Now I get bootmagic to recognize it as 'Linux' but It's listed as 'Not available' when I try to start.
I'm thinking that it is because it's located on another physical disk.

Can someone help me with this issue ? 

Thanks a lot!

---

