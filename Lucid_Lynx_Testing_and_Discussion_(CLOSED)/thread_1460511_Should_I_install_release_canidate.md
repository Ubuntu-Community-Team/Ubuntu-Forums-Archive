---
title: "Should I install release canidate?"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mamamia88 on 2010-04-22
i am thinking of formatting my harddrive since i need it to back up my ps3.  for some reason the ps3 won't read anything but the first partition on the disc and that is ubuntu.  so should i use the harddrive then install lucid?

---

### Post by PGHammer on 2010-04-22
> **mamamia88 said:**
> i am thinking of formatting my harddrive since i need it to back up my ps3.  for some reason the ps3 won't read anything but the first partition on the disc and that is ubuntu.  so should i use the harddrive then install lucid?

Who says you have to choose?

I run Windows 7 Ultimate x64 by default, but I use Wubi (included with 'buntu since 8.04) to ease the pain (while I won't go whole-hog to Linux myself, I still evaluate and use it for some tasks).  With Wubi, you install the buntu of choice from *within Windows* (no GRUB!); instead, your 'buntu shows up in your OS loader.  You set aside a fixed amount of space *within your Windows partition*; other than that, the 'buntu itself uses no extra space.  (The default maximum size is 30 GB, which is a pittance in these days of terabyte hard drives.)  Because it installs within Windows, it can be removed via Control Panel, like any Windows application (it's actually ideal for testing for that reason alone!); other than that, it's still 'buntu, and you use it the same way.
One advantage of Wubi (over traditional testing methods, such as VM-based testing) is that, other than the within-Windows advantages, it's still 'buntu in all other respects (it uses the same drivers as a bare-metal installation; so you can install x64 within x64 Windows, for example, which is what I do); also, unlike traditional side-by-side installs, the Windows partition, and its files, are always available.

No - more - mounting.

If you are nervous about running a non-production-ready OS, then don't do it!  However, if your worries have more to do with leaving the security of Windows and the applications you know, then Wubi makes for a great backstop.

---

### Post by mamamia88 on 2010-04-22
ive been using karmic only on the machine for awhile now.  i already copied all my important data to my netbook so i really have nothing to lose.  might as well play around with other distros until lucid comes out.  anyone know if broadcom drivers work out of the box with this release?

---

### Post by cariboo on 2010-04-22
I would suggest you try out the Live CD to see if your Broadcom device works, with my netbook, I had to plug in a network cable to install the restricted drivers for my bw4312 chip set.

---

