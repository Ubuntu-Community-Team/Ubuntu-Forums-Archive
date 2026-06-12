---
title: "More Help w/ Ubuntu, Please!"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by soluphobe on 2007-07-18
Hello, you wonderful support people!  Thanks for the support I got in my last request.  I won't bore you with the details, but apparently, on my machine, installing Xubuntu makes the Ubuntu LiveCD work great!  I just booted from it for fun, and it booted in less than 5 minutes.  So, I'm trying to install Ubuntu over Xubuntu now, and I'm having some issues in the partitioning section.  I have:

a fat16 16MB swap file for XP,
a ntfs 15GB partition for XP,
a swap file of a couple MB for Xubuntu (now to be used for Ubuntu), and
a 14GB ext3 partition I just formatted that used to hold Xubuntu and I would now like to install Ubuntu to.

When I click 'Forward,'  I first get:

"There are no possible configurations for this FAT type."  Since the only FAT I have shouldn't be touched by Ubuntu, I hit 'ignore.'  Then I get an error about Cluster sizes and FAT sectors.  If I go beyond this, I don't know if Windows will explode or something!  Please, what should I do?

(Sorry if I'm being dumb, but I don't have a clue what these errors mean.)

Edit:  The exact text of the second error is:

"File system doesn't have expected sizes for Windows to like it.  Cluster size is 1k (-537896164k expected); number of clusters is 15954 (225 expected); size of FATs is 63 sectors (-1208930776 expected).

Edit2:  Never Mind...I think everything is okay...I think...

---

### Post by ddrichardson on 2007-07-20
Purely out of interest, why are you using FAT16 for a swap file in XP and why only 16Mb?

FAT16 is notoriously unreliable, has several limitations (2Gb limit even though it should theoretically be 4Gb). Cluster size also varies with partition size which causes other problems. You are also limited to the number of files you can have (512).

I wouldn't worry unduly about this as you wont be accessing it and a damaged swap file in Windows is fairly easily repaired.

The general rule of thumb on Windows (depending on who you speak to) is to have double to two and a half times the system memory available for swap file. The main advantage to a seperate swap partition is obviously to avoid fragmentation problems.

---

