---
title: "RV350 GPU, trouble with X"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by btwThieves on 2012-06-03
Good afternoon,

I'm struggling to get an old computer running Xubuntu 12.04, in hopes of turning it into an HTPC. I've tried installing Ubuntu 11.04, Mythbuntu, and LinHES (basically Arch Linux) but am getting these same results with all variants:

Difficulties with this graphics card have forced me to use the generic "vesa" drivers with this card, which, needless to say, has no 2D acceleration -- a  dealbreaker for an HTPC.

**The symptoms:**
This problem is particularly frustrating because in the course of debugging I have to boot from a Xubuntu CD, mount the hard drive, edit one or two parameters of /etc/X11/xorg.conf or another config file, reboot, enter the BIOS, change boot priority, reboot, and I invariably am rewarded with a blank screen. The connected LCD television displays a completely black screen but does not turn off, and I cannot switch VTs (CTRL+ALT+ F2, for instance). Additionally, I cannot access the machine using its VNC server, indicating a crash in the X server.

**EDIT:** Additionally, I'm not seeing a GRUB2 menu pop up on the screen after the usual BIOS nonsense scrolls by. Even with the VESA drivers installed, the screen simply goes black for about 60 seconds before a desktop suddenly appears. This is happening even after following the instructions on this forum about forcing GRUB to show up (see [http://ubuntuforums.org/showpost.php?p=11469860&postcount=800](http://ubuntuforums.org/showpost.php?p=11469860&postcount=800))

**The problem, as I understand it:**
The computer sports an ancient ATI Radeon 9600 graphics card (with an **RV350 GPU**), for which ATI has long since dropped its support with its proprietary driver (package "fglrx"). **The result is a complete crash of the X server when it tries to initialize the card. **Additionally, the open-source drivers (package "xserver-xorg-video-radeon", aka "radeon") aren't working properly either, despite the fact that this GPU is listed as "supported" by the man page ("man radeon") and the X log (/var/log/Xorg.0.log).

**Relevant logs**
Interestingly, the Xorg log file gives the following error when I use the radeon (open-source) driver:
```
(EE) RADEON(0): No valid linear framebuffer address
```
...and the following error when I attempt to use the fglrx (closed-source) driver:
```
(EE) fglrx(0): No valid linear framebuffer address
```

**Attempted fixes:**
[LIST]
[*]Disabling the framebuffer using kernel parameters, per the wiki article on "Framebuffer"
[*]With fglrx, using the "aticonfig" tool to initialize the card (result: even with the -f flag, it reports "no supported adapter detected" - go figure...)
[*]COMPLETELY removing fglrx before attempting to use radeon
[*]Disabling kernel mode-setting by booting with the "nomodeset" parameter
[*]Setting the "modeset" parameter of the radeon module to "1" or "0"
[*]Setting the "AGPMode" parameter of the radeon module to -1, 0, 1, 2, 4, or 8
[*]Disabling various options of the radeon module (ColorTiling, etc.)
[/LIST]

**The last resort** (what I'm trying to avoid)
In the event that this graphics card issue cannot be resolved, I'll try to revert to Ubuntu 8.04 -- the last version of Ubuntu with a kernel and X server version low enough to be supported by ATI's proprietary drivers. Whether or not this will work is another question; if it doesn't, I'll be forced to reinstall Windows XP -- which would simply break my heart, being an adamant Linux enthusiast. Therefore any help you can give me is very much appreciated!

Thanks,
betweenThieves

---

### Post by btwThieves on 2012-06-04
Bump... Really don't want to install windows again...:(

---

