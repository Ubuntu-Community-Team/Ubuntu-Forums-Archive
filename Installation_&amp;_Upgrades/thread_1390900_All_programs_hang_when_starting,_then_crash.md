---
title: "All programs hang when starting, then crash"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by sko77sun on 2010-01-26
I have tried three fresh installs of Ubuntu 9.10 using an ext4 formatted hard disk. I experienced this issue with one hard disk, so tried a fresh install on another, but I get the same issue. When Ubuntu boots up I can get Termimal to start, but no other programs, even when I try to open folder, it flashes momentarily, then disappears. Each program says "Starting {program name}" in the bar at the bottom of the screen, hangs then disappears. I really want to start using Ubuntu, it is odd as everything worked fine with the Live CD, but not when installed to hard disk.

I have also tried "sudo apt-get install -f" and it first tells me "segmentation faultsts... 22%", then if I try this command again, the console outputs "Segmentation faulty tree... 50%"

Any ideas?

---

### Post by tommcd on 2010-01-26
Are you able to boot to the Ubuntu graphical desktop? And then the only program you can open is the terminal? Is that correct? Or do you not even get to the graphical desktop at all? This sounds a bit strange. 

First, just to rule out a bad install CD as the source of the problem, boot up the CD you used to install Ubuntu and run the option "check disc for defects". If the CD passes, then it is good. Report back the results of this.
If the CD is good, then try running some programs from the terminal and post what error messages you get. For example, to run Firefox, simply type **firefox** in the terminal and hit enter. To run the Totem video player, simply type **totem**. Report what errors you get.
This should hopefully provide enough info to help diagnose this.

And welcome to the Ubuntu forums!

---

### Post by Sef on 2010-01-26
If you can open the terminal, copy and paste this command:

> sudo dpkg --configure -aIf you  cannot open the terminal, do this:

alt + F2 > gnome-terminal

If you get any error messages (other than what you have had), copy and post them please.

---

