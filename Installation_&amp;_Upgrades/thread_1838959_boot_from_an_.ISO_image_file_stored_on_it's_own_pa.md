---
title: "boot from an .ISO image file stored on it's own partition"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by w1av on 2011-09-04
Hi,

I am wondering if it is possible to have an additional BOOT OPTION from GRUB when computer starts.......Right now I have a dual boot (Ubuntu 10.10 and WinXP). I have a spare partition that is not really used and I was thinking about if it is possible to put an .ISO image of, say Ubuntu 11 on there. How can I get GRUB to recognize it at boot time and have that as an option to boot from??????  I tried this once before many years ago with another distro and it worked very well. Since the image is on a dedicated partition, it should boot VERY FAST. This would be helpful in times that I need to quickly check email and Craigslist without wasting too much time when I am busy. I am not sure what to do, and I am not the "geek" like I used to be. Please help!!!!:confused:

---

### Post by oldfred on 2011-09-04
I do this for installs either from my sdb drive to install into sdc or my flash drive which looks like another drive in my system.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

