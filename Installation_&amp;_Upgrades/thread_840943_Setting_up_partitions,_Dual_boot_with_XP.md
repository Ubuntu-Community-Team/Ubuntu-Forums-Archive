---
title: "Setting up partitions, Dual boot with XP"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by MichaelSelf on 2008-06-25
I'm trying to install Ubuntu 8.04 on a second desktop in my house.  For my last installation I simply did away with XP and formatted the disk during the installation.  

For this install I want to dual boot with XP (family computer) and I wish to share a third partition formatted to FAT32 between Ubuntu and XP.  

Additionally I've read into /home and swap partitions, but I'm not sure exactly how they all work.  I understand that a /home partition will allow me to save all my settings and such so that I can perform a clean install of Ubuntu if needed (I'm still pretty new at all this so it's probably a good idea I believe).  And if I understand correctly (which I may not) a swap partition will help out with loading files, etc.

What I need help with...
When I go through with the install how should I go about partitioning the HD manually with the setup?  My HD is a 160 Gig and apprx 80 Gigs are used.  I do not want to loose my files b/c I lost my XP disk and it's the family computer.  

Should I partition the HD before hand (I use Acronis Disk Director and it seems to work pretty well for me) or do it through the Ubuntu Setup


Ideally I want this setup I believe (comments/suggestions welcome)


C drive - XP (NTFS) | J Drive - Shared Storage (FAT32) | /home (ext3) | Ubuntu (ext3) | swap

---

### Post by Pumalite on 2008-06-25
This might help:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by MichaelSelf on 2008-06-25
that's one of the pages that I've gotten the ideas for how I want my partitions to be set up.  My problem is based on the process of setting everything up.  

What size should the different partitions be?
Should I set them up myself using Acronis Disk Director, or use the Manual option during installation?
  - How do I use the manual partitioner in the installation?

---

### Post by Pumalite on 2008-06-26
Use Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Shrink XP (right click on partition. There is a limit of 4 primaries per drive. You might have to delete one and make an extended partition. Inside of this you can have as many logicals as you want. Ubuntu loves logicals. For Ubuntu:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home
Then install, go Manual and choose the already prepared partitions.

---

