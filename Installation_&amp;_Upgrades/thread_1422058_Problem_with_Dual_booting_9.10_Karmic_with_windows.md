---
title: "Problem with Dual booting 9.10 Karmic with windows 7"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by Mogrim on 2010-03-04
I have seen this post.
[http://ubuntuforums.org/showpost.php?p=5731340&postcount=7](http://ubuntuforums.org/showpost.php?p=5731340&postcount=7)
But, this doesn't help me, sorry. I am pretty sure someone else has had my problem so could someone direct me to that post or tell me how I am messing things up. 

Computer:
AMD 939 Athlon 64
Biostar 6100T Motherboard
Windows 7 Enterprise 32 bit
1tb Seagate hard drive

I did the install from the 64 bit edition Ubuntu 9.10 Karmic Koala iso file and when I restart is gives me the no root file system is defined. Please correct this from the partitioning menu. Unfortunately I don't know if it means the window installation or the Ubuntu one. I also don't know exactly how to get to it if it isn't the windows one. Any suggestions would be nice because I also want a triple boot with Windows XP Professional SP 3 32 bit.

---

### Post by oldfred on 2010-03-05
Run this script to see your configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.


Windows combines its boots into one, if you want to directly boot each copy of windows see this:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

