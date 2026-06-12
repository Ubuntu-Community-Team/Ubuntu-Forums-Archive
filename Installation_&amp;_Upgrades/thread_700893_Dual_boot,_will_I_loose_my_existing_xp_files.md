---
title: "Dual boot, will I loose my existing xp files?"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by Kevin Jones on 2008-02-18
Hello all,
I want to install Ubuntu 7.10 on an old HP pc.
I have windows XP as an operating system, with plenty of files that I do not wish to loose.
I have read some online instructions for dual booting, and they seem to suggest I will lose the memory if I choose to download the Ubuntu
Can some one point to the correct way to NOT WIPE MY HARD DRIVE! and download ubuntu to co-exist with Windows XP 
thanks 
Kevin

---

### Post by blackbinary on 2008-02-18
Nope, you won't loose your XP files if you do it right.

All you need is enough room for ubuntu. I left 20GB for mine, some say you can easily get it down to 5GB. Your XP files and installation is in format NTFS(normally). This is fine for Ubuntu to read and write these files, but its installation needs to be ut3. So you need to create a 5GB min partition in the ut3 format for ubuntu to install to. if your trying to make it as small as possible, don't put any files in /home, put them in a folder on the NTFS format partition.

Hopefully thats clear. all you need is to have empty space for ubuntu to fit.

---

### Post by Pumalite on 2008-02-18
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Resize XP partition by right clicking on it and choosing 'resize' from the menu. The format is ext3. I recommend you leave at least 20 GB for Ubuntu. 
Backup all important files first. (a matter of good practice)

---

### Post by blackbinary on 2008-02-18
Actually Puma, the Ubuntu Live CD has gparted on it, you can partition your drive, then click install on the desktop, and way you go.

---

### Post by Pumalite on 2008-02-18
The Gparted Live CD, the stand alone program, is newer, more powerful, more flexible and easier to use.

---

### Post by Kevin Jones on 2008-02-19
great stuff!!!
I have downloaded the gparted and created a live cd. I am, as we speak, waiting for the partitioning to finish.
I had some trouble with the gparted, in that it did not recognize my video card
# Forcevideo did the trick, followed by # vesa followed by the resolution (all this was prompted by the gparted cd... which is great.
Last question:
Ubuntu by default uses ext3.
When I format the enlarged, but unallocated partition do I make it ext3 (if that is possible) or ut3?
thanks for the great help

Kevin

---

### Post by Pumalite on 2008-02-19
Make it ext3. Or; with the new space you can create 2 partitions:
At least 10 GB for '/'
1 GB for /swap
(if you had more space you could create another one for /home)

---

