---
title: "Ubuntu Xwindow Crash?"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by Wej on 2006-07-04
This is the first time I've ever tried Ubuntu, and I seem to be having problems. My goal is to dual boot this system with WinXP + Ubuntu. I downloaded the latest version of Ubuntu today, 6.06 Desktop via the torrent file. It boots from the disc without a problem, but after it goes through the driver loading process and takes me to the red gradient screen, a strange multicolored bar appears on the screen. Looks to me like an X window problem. The mouse cursor switches from the x to the arrow pointer, but I can't do anything. It just sits there as long as I let it. Here is a picture I took with my camera, it's dark in here, so it's not that great of detail.
[[IMG]http://img84.imageshack.us/img84/8197/ubuntuborked6aq.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=ubuntuborked6aq.jpg)

System specs as follows:
AMD X2 4200, EPoX 9NPA+ (nforce4 ultra chipset), GeForce 7800GT, 2GB DDR 400, 1xPATA 300GB, 2xSATA 300GB; JBOD.

Any ideas about how to get around this? I will try installing it on my system at work when I get some free time there, but I would like to test it out on my home system where I don't really mind screwing something up. :)

Thanks

---

### Post by rpdillon on 2006-07-04
Try getting more info by checking the console with Ctrl-Alt-F1 or Ctrl-Alt-F2 (I forget which console the liveCD uses).  Check any error messages and google for those phrases (with quotes around them!) or post them here.

It could be the way X initialized...try Ctrl-Alt-Backspace to kill the server and see if it comes back any better.  I had a problem with that one one of the boxes I ran the liveCD on.

If that doesn't work, go with a text install from the 6.06 "alternate" CD/DVD, which is really more of a "backup"/"advanced" CD/DVD.  I used it to install to a RAID0 setup.  Sadly, its another download, but it should get you installed.

---

