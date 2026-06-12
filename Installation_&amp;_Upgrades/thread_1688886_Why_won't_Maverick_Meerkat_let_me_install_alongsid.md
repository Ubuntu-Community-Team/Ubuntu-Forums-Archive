---
title: "Why won't Maverick Meerkat let me install alongside windows"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by DrEagle22 on 2011-02-15
i had removed ubuntu from my laptop a while ago and now i want to install it back on my hard drive....now i try to do it and it wont give me the option to install alongside other operating system...it only gives me the option to erase partition and install ubuntu or manually specify partions....but im not smart enough to do it

if someone could help...that would be awesome

---

### Post by GWBouge on 2011-02-15
Did you have a Wubi install before, or had you set up a separate partition?  Can you use the option to 'Use the largest contiguous free space' (I think ...) ?

To install along side Windows, I believe you're going to have to do a Wubi install.  Boot into Windows, pop in the Ubuntu disk, and follow the directions for installing Ubuntu without any changes to Windows or you hard disk.

I wouldn't recommend doing that for any long term installation, though.  If this is something you plan on keeping, you can use the Gparted utility on the LiveCD to resize your Windows partition and make room ffor an ext4 partition for Ubuntu to use.

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions")
[https://help.ubuntu.com/community/GParted]("https://help.ubuntu.com/community/GParted")

---

### Post by thefasterblueone on 2011-02-15
This is really not too difficult. read the whole tutorial first and then take your time, be absolutely sure of each step.:popcorn:

[http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/]("http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/")

---

### Post by sikander3786 on 2011-02-16
For an overview of changes in the new installer, see here.

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

For manual partitioning, see the link at the bottom of my post "Manual partitioning Natty". It is intended both for Natty and Maverick.

---

