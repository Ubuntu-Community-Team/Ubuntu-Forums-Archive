---
title: "Xubuntu hangs during boot"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by travlemon on 2012-01-31
Hello,

_**The Problem:**_
I just installed a fresh copy of Xubuntu 11.10 on my laptop, the system is dual booted with Windows XP.  I had everything working great, including the installation of my favorite software and copying over software profiles into my home directory, and my documents.

The only two things I had left to straighten out were system updates, and adding a line to xorg.conf to fix Powermizer on my Nvidia graphics card.  So I simply let update manager run and install updates, then I created a xorg.conf files with nvidia-settings (Ibelieve there is no xorg.conf file by default in 11.10).  I updated xorg.conf how I always do, after I created a new one.

When I restarted my system, I was greeted with the Xubuntu loading screen and the loading bar frozen on about 1/5 of the way through.  It freezes pretty much immediately, and hitting CTRL + ALT + (F1, F2, F3, etc) doesn't help me. 

_**What I've tried so far:**_

1.  Thinking that incorrectly modified xorg.conf (I accidentally leave a typo in it from time to time), deleted the line that I added before the reboot.  No Luck.

2.  I tried removing xorg.conf altogether, to eliminate any possibility of something quirky being in the conf file.  The system originally had no xorg.conf, so I figured this would work, if the problem was video related.  No Luck again.

3.  My boot loader has a "Previous versions" entry that allows me to boot into older kernel versions.  None of these would boot for me.

4.  I tried running **sudo apt-get install --fix-broken** to fix broken packages, in case the updates went sour.  I'm not sure if I even have the syntax correct on that command.

5.  I tried booting into recovery mode and choosing the option to fix broken packages, and then the option to clean after that.

**_Conclusion:_**

I'm out of ideas!  I'm probably just one step above a complete novice Linux user, so I'm not really sure where to go from here.  Any suggestions on this would be much appreciated!


***NOTE:** This may be nothing, but if I choose the recovery mode from the GRUB menu and then choose to resume a normal boot, the system still does not boot, but it produces an error when pressing CTRL + ALT + F7 for the graphical mode:

**INITCTL: EVENT FAILED**

**EDIT:**  I have more information.  When I press ESC on the keyboard during the splash screen (I only have seconds to do it, before it freezes), I can view the command line while the system starts up.  The very last line, before the system hangs, is ***Starting TiMidity++ ALSA midi emulation. . .    [OK]**.   Then I am left with a blinking cursor and the system never moves on.

Again, any help is much appreciated.  Thanks in advance!

---

### Post by djmac on 2012-02-01
Hi travlemon,

I believe I had literally the exact same problem just this morning (though with Ubuntu 11.10, and freezing at the purple screen with dots). Unfortunately my solution may not work for you... (if you don't have a backup or previos version of your xorg.conf) 

I tried virtually the same things as you. Even got the **NITCTL: EVENT FAILED** error (after trying to login from recovery mode). Fortunatley I was able to replace the modified xorg.conf with a backup, which seemed to fix the problem (on restart). 

I am not sure what you should do without an xorg.conf.backup file - but hopefully it may point you in the right direction - though it looks as though you may have already tried doing something about this. Maybe someone else will have a suggestion...

Cheers,

djmac

---

### Post by travlemon on 2012-02-03
> **djmac said:**
> Hi travlemon,

I believe I had literally the exact same problem just this morning (though with Ubuntu 11.10, and freezing at the purple screen with dots). Unfortunately my solution may not work for you... (if you don't have a backup or previos version of your xorg.conf) 

I tried virtually the same things as you. Even got the **NITCTL: EVENT FAILED** error (after trying to login from recovery mode). Fortunatley I was able to replace the modified xorg.conf with a backup, which seemed to fix the problem (on restart). 

I am not sure what you should do without an xorg.conf.backup file - but hopefully it may point you in the right direction - though it looks as though you may have already tried doing something about this. Maybe someone else will have a suggestion...

Cheers,

djmac


Hey, thanks for responding!  Sorry for such a late response, I got the email notification when I was really busy and forgot about my post.

I ended up reinstalling the system and installing all of my software all over again.  I was more careful about editing xorg.conf, and had no problems this time.  That file can be very picky about having an extra space at the beginning or end of a line.

Anyway, I'm all fixed and I'll mark this as solved.  Thanks for responding!

---

