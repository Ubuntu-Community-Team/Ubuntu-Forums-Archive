---
title: "Newbie Install Questions: Partition Settings, etc."
date: 2005-02-03
forum: Installation &amp; Upgrades
---

### Post by Jcoldslabs on 2005-02-03
I have been able to run both the Warty and Hoary Live CDs and decided to try a real install of the Warty release.

My c: drive (in Windows) is my boot drive (Western Digital 250GB) and I set aside a 20 GB fat32 partition to use with a Linux install. 

When trying to install Ubuntu onto this partition I get to the "Partition Settings" screen and have NO IDEA what settings to use for the following:

Usage method: ?
File system: ?
Mount point: ?
Mount options: ?
Bootable flag: ?

Rather than waste too much forum time, is there a link or a FAQ or help file that would answer these questions for me? 

System info: Epox 8RDA6+ motherboard, nVidia nForce 2 Ultra 400 chipset, AMD Athlon 2700+ processor, 1 GB RAM

Thanks.

J.

---

### Post by ctt1wbw on 2005-02-03
Can linux go on a fat32 partition?  I thought it had to be ext2 or something like that.

---

### Post by Juergen on 2005-02-03
FAT is not good for Linux. You could fiddle around with UMSDOS, but why?

Best is to install to empty space, so delete your fat partition.

I don't know ATM if the Ubuntu installer has an easy option to install to empty space
- if not you might want to read [http://www.tldp.org/HOWTO/Partition/](http://www.tldp.org/HOWTO/Partition/) 

For a start you might try
/ - 6GB  - reiserfs
swap -  512MB - swap
/home - rest of the free space - reiserfs

Later, depending on the things you do with your box, 
you might want to re-install with seperate partitions for /var and/or /usr and so on,
but the above should be OK for your first experiences

---

### Post by Jcoldslabs on 2005-02-03
Thanks for the advice. I had heard from someone else that I needed a fat32 partition for Linux. I'll go back and start from scratch without any formatting and see what happens. 

J.

---

### Post by Neo_654 on 2005-02-03
They may have meant that it was easier to share a fat32 partion between the two OS's.  So that both OS's can read and write to the same drive.

---

