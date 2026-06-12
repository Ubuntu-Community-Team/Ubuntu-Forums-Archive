---
title: "Laptop with higher CPU usage after upgrade to 7.10"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by jwh2505 on 2008-02-24
My laptop is an Asus M2400E with Pentium 4-M at 1.8 Ghz and 640 RAM, which ran both 6.10 and 7.04 without any hitches.  After upgrading, after Gnome loads, top shows CPU usage at idle is from about 7-35%, and the fan runs at a much higher rate than before. Top shows Xorg with the highest percent of CPU usage, at anywhere from about 7-13%.  If I begin opening programs, the total CPU usage quickly jumps to 90%+, and som programs seem to load considerably slower than before.  My desktop, (Intel Celeron at 2.0 Mhz, 512 RAM) still has 7.04 installed and the idle CPU usage on it is 1-2% and programs open speedily.

Initially after upgrade, boot up also seemed much slower, but after deleting Usplash as recommended on another thread, boot up is faster, but the CPU usage has remained the same.  Also, since removing Usplash, after Gnome loads, the screen goes blank and I have to manually adjust the brightness control in order to see the desktop.

Thanks in advance for any help.

---

### Post by jmate24 on 2008-02-24
use Xubuntu 7.10's alternate CD. and install it. it uses less resources and you can install your gnome or KDE applications. [HTML]http://www.xubuntu.org/[/HTML]

---

### Post by jwh2505 on 2008-02-25
Thanks for the suggestion.  I downloaded and installed the Xubuntu desktop via Synaptic this morning and have been trying it out, but it hasn't made much difference.  I still have a similar CPU usage, and delays when loading and using programs.

I did notice this morning on a reboot that the fan kicked in at high speed during the boot process, causing me to think something was beginning to hog the CPU at that point, confirmed by a slow loading GDM.  Is something messing with the kernel?

---

### Post by analphabuntu on 2008-02-26
hello everybody.
I have exactly the same problem!!!
I installed ubuntu 7.10 on my asus L3500D laptop. the system boots fine but after a few minutes the CPU usage raises up to 99-100% even if no application is running, it all becomes sloooooow and fan gets crazy.
my specs:
asus L3500D, amd athlon xp 1800+ 1.5GHz, 1.5 Gb ram, HD 60Gb with just ubuntu on it (no dual boot).
any idea?
thanks.

---

### Post by monkeybrain on 2008-02-29
I've got an M2400E as well and also have this problem. The thing is I've had the problem before and fixed it, but now I've done a clean install and the problem is back. I'm sure the issue is connect to the hard disk and something about hda or sda in the new kernel. I think the fix was editing a file. Apart from that I can't remember! Someone help us!

---

### Post by jwh2505 on 2008-03-01
I gave up and did a fresh install of 7.04 on my machine.  It now runs faster than when I had 7.04 on it before as an upgrade to 6.10, so I'll keep it this way until someone can give us a definitive answer of how to solve the problem in 7.10.

---

