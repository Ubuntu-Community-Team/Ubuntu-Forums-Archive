---
title: "X/Ubuntu hangs on boot, can't install"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by Drone4four on 2011-11-03
The LiveCDs for Xubuntu 11.10 32bit, Xubuntu 11.10 64bit and Ubuntu 11.10 32bit hang just before the Desktop loads preventing me from using an applications like Ubiquity.  for example. The O/S gets to the point where I can do an ALT + F2 and type firefox.  Firefox loads but then the whole O/S just hangs before I can enter a website URL or use Google.  After it hangs, the hard drive and CD drive stop. I even tried CTRL + ALT + F1-F7 so I can login as root and start up top.  But even top stops updating and I can’t switch to other virtual terminals.  How could I better describe my problem?  I am writing this forum thread on my existing Xubuntu 11.04 64bit.

---

### Post by darkod on 2011-11-03
Looks like video driver related. I'm not sure, but I think when booting with the CD, at the first menu you could hit F6 for advanced options. Try to add nomodeset at the boot command and see if it boots successfully into live mode.

Don't have the CD and can't check right now if it was F6 and where was the option exactly.

---

### Post by Drone4four on 2011-11-03
Thank-you darkod, I am writing this post from a successfully booted Xubuntu LiveCD.  Pressing F6 at the first menu upon boot brought me to Other Options. After selecting nomodeset Xubuntu loaded perfectly.  Does this mean that it was a video problem?  I guess that would sort of make sense because I am running an nVidia GTX 560 Ti which is pretty bleeding edge.  darkod:  How did you arrive at this solution? I ask because I would like to be self-reliant and figure out these things on my own.  Thanks again.

---

### Post by darkod on 2011-11-03
I personally never had this issue, but I have seen it here on the forum. And the solution, I didn't think of it. :)

Note that after the successful install you might still need to use it to boot successfully. If you do, in the grub menu at boot just highlight the ubuntu entry, hit 'e' to go into edit mode, and add nomodeset at the end of the line starting with linux. Press Ctrl + B to boot.

If you need to make it permanent you need to add it into /etc/default/grub, change the line saying:
GRUB_CMDLINE_LINUX=""

to "nomodeset". After that run sudo update-grub to update it.

In this line you can also add other commands that you want to add to the boot line if you need them.

---

