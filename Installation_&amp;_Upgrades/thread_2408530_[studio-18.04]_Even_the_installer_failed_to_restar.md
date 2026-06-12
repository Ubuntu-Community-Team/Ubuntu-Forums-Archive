---
title: "[studio-18.04] Even the installer failed to restart..."
date: 2018-12-19
forum: Installation &amp; Upgrades
---

### Post by AvantGuy on 2018-12-19
Dear colleagues, 

Linux noob, glad to be here and to make my first post. Searched the forum and noted the "popularity" of shutdown issues, but none posted seemed to match mine. However, I did try a couple of the solutions/workarounds posted, and I think they may be hints.

The issue:[INDENT]
I just did a clean install to sdb (an SSD; sda has W-10). Installer seemed successful but it would not restart (at the end of its installation process, it locked up the moment I clicked OK to restart on the final dialog). 

Same issue with the system- it appears to run perfectly, but attempts to shutdown normally via the gui (and several from the terminal) similarly locks up right where it sits (i.e., no on-screen updates after the moment I click, or when hitting enter if attempting from terminal)
[/INDENT]

I've tried various things, including...[INDENT]     [FONT=courier new]
[SIZE=3] sudo swapoff -a && systemctl poweroff[/SIZE][/FONT]
    (this failed, locking up the moment I hit ENTER)    

    [SIZE=3][FONT=courier new]Sysrq: reisub[/FONT][/SIZE]
    (succeeded)
[/INDENT]
     
I'm glad reisub is a success, but I hope for help fixing the underlying issue.
    
Thanks, Bob (Linux noob)
[RIGHT][FONT=courier new][ubuntuStudio] 18.04, x64, Asus 17" notebook
GL752VW, i7-6700HQ, 16Gb, dual boot[/FONT]
[/RIGHT]

---

### Post by The Cog on 2018-12-19
Out of interest, does it power off with **Sysreq: reiuso **?

---

### Post by AvantGuy on 2018-12-19
> **The Cog said:**
> Out of interest, does it power off with **Sysreq: reiuso **?
No. Utterly no effect (system remains in normal state - fat and happy). Same as sysrq: reisuo

---

