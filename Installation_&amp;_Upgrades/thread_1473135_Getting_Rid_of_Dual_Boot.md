---
title: "Getting Rid of Dual Boot"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Cathhsmom on 2010-05-04
Having used Ubuntu for about 6 months,and not using Windows but a handful of times, I am seriously thinking of getting rid of Windows altogether. I came upon this decision with a goal of cleaning up my computer with a clean install/s of operating system/s. I have 8 gigs left on my hard drive on my laptop.  

My thinking is that my computer will be more optimized by having one system.  I can see all of my files all of the time.  I hated not being able to see my Linux files while I was in Windows.  

I have thought about buying a new larger internal hard drive to accommodate my files space need while keeping both Windows and Linux.  Then thinking about how I cannot access my linux files easily on Windows, I thought about buying portable hard drive and place all my files on this  with my operating system/s on the internal drive.   Then I thought about just having Linux with no Windows.   

Can I have some help with thinking about the pros and cons of each setup?

---

### Post by chejrw on 2010-05-04
For what it's worth, you can rather easily access your linux files from within Windows by installing EXT2/EXT3 drivers for windows - this is assuming you're using the default EXT2/3 filesystems and not something exotic like ReiserFS.

Whatever route you persue, I'd suggest keeping files you access often on internal drives - external drives are not designed to run all the time and using them as 'always on' drives is just asking for a catastrophic drive failure and data loss - use one for backups, or for storing media you use occaisionally by all means, but don't mount your home directory on one.

If you're not completely ready to go M$-free yet, my suggestion might be to have your /home directory(ies) on a separate partition, and mount that partition as a drive in Windows as well (you could even mount the windows 'My Documents' folder to that drive).  Keep all of your personal files there.  Just a warning - windows will ignore file permissions and will generally write things as 'root', so you may run into some minor issues with permissions flipping back and forth.

---

### Post by paynek716 on 2010-05-04
Why not get a larger hard drive, then add a /data partition to the disk in NTFS format? This would provide a shared space that can be accessed by both Windows and Linux.

You can also get an external case for the old hard drive. Now you've got an external hard drive, great for backups.

---

