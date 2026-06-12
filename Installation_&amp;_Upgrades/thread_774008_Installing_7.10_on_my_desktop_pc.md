---
title: "Installing 7.10 on my desktop pc"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by matthewhunt on 2008-04-29
I've tried and so far failed to get 8.04 to run on my desktop pc, I keep getting dropped to the busybox so i'll leave that version alone for now and perhaps upgrade from inside 7.10. I have got 7.10 running from the live CD on my desktop pc, but the keyboard doesn't work. It runs ok in Win XP, and works outside of the desktop environment, but as soon as the desktop appears the keyboard is dead. 

My other issue is with installation. My second IDE drive is already partitioned and i have a partition which i have cleared for linux use. Do I need to delete the partition and reformat it? and what is the native file format for linux. I guess it isn't fat32?

I feel like a complete noob with this, well in linux terms i am but i look forward to moving away from microsoft. I just don't like vista and it's DRM implications, and xp swallows up my computers resources in no time at all.

---

### Post by Kevbert on 2008-04-29
I suggest you do a hunt for your keyboard type on the forums. Is it wireless ?
Regarding installing Ubuntu, you could perform a guided install on the empty partition when running the CD. This will set up the formatting/any additional partitioning. 
For a manual install (instead of guided) I suggest you allocate around 10Gb for system files and at least twice the amount of RAM you have to the swap file (say 2Gb).  The partition format for system files is ext3.  The swap file is used for system crashes (if any ever occur).

---

### Post by matthewhunt on 2008-04-29
My keyboard is simply a normal ps/2 keyboard. No fancy shortcut buttons, a packard bell badged unit circa 1995ish. Still works so i'm happy. I'm using a wireless USB mouse at the same time so not sure if having the two different types is causing a problem. I might borrow a USB keyboard (or ps2 mouse) to see if that solves the issue.

The guided install only suggested using the full second ide drive not individual partitions so I may spend time moving my data to my primary ide and having a fresh drive to install ubuntu to.

---

### Post by dstew on 2008-04-29
It might not be too hard to get that 8.04 Live CD to run. There are kernel parameters that you can try. What system is your PC? Maybe somebody out there has experience getting the Hardy Live CD to boot.

One reason for telling you this is that a clean install is usually easier and better than an upgrade from inside a previously installed system. So, if you get 7.10 installed, then upgrade to 8.04, you may have issues. I think some effort at getting the 8.04 CD to run will give good returns. There is also the 8.04 Alternate Install CD. It installs the same Ubuntu Desktop, but uses a text-based installer that works more reliably than the Live CD.

About your keyboard, if you have an installed 7.10 system, try```
sudo dpkg-reconfigure xserver-xorg
```from the Recovery Mode command line to set-up the keyboard again. This takes you through some of the same steps you went through during installation. Maybe you can get it to work in the desktop this way. After reconfiguring, enter **startx** if you booted into recovery mode.

---

### Post by matthewhunt on 2008-04-30
I haven't managed to install 7.10 yet because you need the keyboard to enter some of the settings such as user migration etc wich it won't let me . I have a funny feeling it's some conflict because i'm using a usb mouse and a ps2 keyboard. I may try different combinations of keyboard/mouse to achieve a hardware solution. I guess there's no command line options that would force use of the ps2 keyboard in the desktop environment.

---

### Post by matthewhunt on 2008-05-01
OK, managed to sort the keyboard issue, I'm now using a USB keyboard and it works fine so that issue is sorted. I think it was a ps2 conflict ue to a message that came up while i was trying different command line entries to get hardy to install, which still doesn't work with the new keyboard.

---

