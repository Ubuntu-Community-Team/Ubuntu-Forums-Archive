---
title: "Install Ubuntu 10.04 Beta 2 On EXTERNAL HARD DISK"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by SkullTraill on 2010-04-13
Can someone provide me with a detailed tutorial on how to install Ubuntu 10.04 onto a EXTERNAL HARD DRIVE [USB], and run it.

I know it might have something do with Wubi, I have the latest release, just please give a detailed description of how to install it and use it on a EXTERNAL HARD DRIVE [USB], Perhaps link me to a tut?

Thanks

---

### Post by SkullTraill on 2010-04-13
Aw come on some body!

---

### Post by SkullTraill on 2010-04-14
Why is noone helping me?

---

### Post by that1dude123 on 2010-04-23
I'm going to try and figure this out. I'll tell you what I found out, as soon as I can. :)

---

### Post by abra1 on 2010-04-23
read this - it should help:

[http://ubuntuforums.org/showthread.php?t=1460339](http://ubuntuforums.org/showthread.php?t=1460339)

---

### Post by oldfred on 2010-04-23
You mentioned wubi which is not a normal dual boot. You should just do a standard dual boot install to your external hard drive. What is on your external currently and do you want to save any of it. Do you have space or are you deleting something. 

The main thing with an external is to use the advanced button to make sure grub is installed to sdb ( or whatever your external is) not to the internal. Otherwise you will have to always have the external plugged in. The you set your BIOS to boot the external first and it will boot Ubuntu, if not plugged in it will boot your internal.

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

The main thing in the tutorials you find is the difference between grub and grub2. Make sure of which you are using and then only follow instructions for that if you have any issues where you have to reinstall grub(2).

---

