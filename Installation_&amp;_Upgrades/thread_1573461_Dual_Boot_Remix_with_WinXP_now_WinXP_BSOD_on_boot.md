---
title: "Dual Boot Remix with WinXP now WinXP BSOD on boot"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by jcguidry on 2010-09-12
I just installed Ubuntu Remix 10.04 on my wifes MSI U100 netbook.  I did a dual boot just in case she had to get into Windows for something. I let the install automatically partion (did the side by side option).  Anyway, Ubuntu works fine and imported all her documents and stuff.  Problem is Windows XP won't boot.  The first time I tried to boot Windows XP I got a message saying the hardware had changed and I had to select safe mode, normal boot, last known good, etc...  I booted normally.  I got the splash screen followed by a quick flash of BSOD and a reboot.  I does this no matter how I try to boot Windows (safe, command prompt, etc).  Anyone have any idea what the problem is?  The file structure appears to be in place so I'm puzzled what the problem is.

TIA,
Jason

---

### Post by Troublegum on 2010-09-12
Probably because the windows partition has been resized. 
I'd try booting the winxp cd and run chkdsk from the windows recovery console. If that does not help, try the repair option from the windows xp cd.

---

### Post by jcguidry on 2010-09-12
Thanks.  It's a Netbook so no DVD drive and I don't have an external one.  Guess I'll have to figure out how to make a bootable USB drive to fix it.

---

### Post by wilee-nilee on 2010-09-12
> **jcguidry said:**
> Thanks.  It's a Netbook so no DVD drive and I don't have an external one.  Guess I'll have to figure out how to make a bootable USB drive to fix it.

You can set up a chkdsk from the safe mode choice gui choose the command option. You actual get to this screen by booting the computer then choose XP then start tapping the f8 key to get there=safe mode gui.
[ATTACH]169310[/ATTACH]

In the command run chkdsk /p/r
The terminal will ask you if you want this done on restart say yes the reboot XP.

Now if you want to load a thumb with a legit XP here is a program that has worked every time for me, has to be run in MS though and has to read the install cd.
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)

It just so happens I have a link to a legit XP ISO as well.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

