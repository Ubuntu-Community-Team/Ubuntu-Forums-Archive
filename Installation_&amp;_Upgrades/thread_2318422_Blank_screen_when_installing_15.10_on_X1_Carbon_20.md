---
title: "Blank screen when installing 15.10 on X1 Carbon 2016"
date: 2016-03-26
forum: Installation &amp; Upgrades
---

### Post by garnavis on 2016-03-26
Hi all, I just got my Lenovo ThinkPad X1 Carbon 2016 and I'm trying to install Ubuntu 15.10 on it. I'm not very experienced with this sort of thing. I followed the basic instructions from the Ubuntu website (using the Universal USB Installer). I can load to the USB drive from the BIOS and I get the options to try Ubuntu, install Ubuntu, or check the hard drive for defects. I've tried loading each of these and each time, the screen goes black and nothing seems to happen. I waited for a while before holding down the power button to turn it off and try again. I'm not really sure what to try next. Any help? Thanks!

---

### Post by T.J. on 2016-03-26
> **garnavis said:**
> Hi all, I just got my Lenovo ThinkPad X1 Carbon 2016 and I'm trying to install Ubuntu 15.10 on it. I'm not very experienced with this sort of thing. I followed the basic instructions from the Ubuntu website (using the Universal USB Installer). I can load to the USB drive from the BIOS and I get the options to try Ubuntu, install Ubuntu, or check the hard drive for defects. I've tried loading each of these and each time, the screen goes black and nothing seems to happen. I waited for a while before holding down the power button to turn it off and try again. I'm not really sure what to try next. Any help? Thanks!

My guess is that your graphics driver is not working properly. You could try passing "nomodeset" to the bootup parameters by pressing "e" on the bootentry to edit it.  There are lots of instructions on web for this, but if you need a more detailed explanation, please ask.  The nomodeset should help in diagnosing your problem.

If your laptop is meant for business purposes, I'd consider Debian 8 or Ubuntu 14.04, then perhaps switch to Ubuntu 16.04 when it becomes available.  Ubuntu 15.10 is a short term release intended for developers or users who don't mind a few bugs.

---

### Post by castrinho8 on 2016-03-30
I have the same problem so I used "nomodeset" but this attached screen appears and nothing more happen :(

I'm thinking about some graphical issues but I don't know, I tried Ubuntu, Fedora and Manjaro and I have the same problem with all distributions.

---

### Post by Wayne_Anderson on 2016-03-31
[COLOR=#000000][INDENT]If you have the option, change the option os windows 8.x to windows 7 in the bios.

See 2nd pic here: [http://www.guruht.com/2014/09/how-to...sus-x200m.html]("http://www.guruht.com/2014/09/how-to-install-windows-7-on-asus-x200m.html")[/INDENT]


[/COLOR]

---

### Post by castrinho8 on 2016-04-03
Thanks for the info but there isn't any option in the bios to select windows 7.

Some friend told me that maybe it is a problem with the new intel hardware support in actual kernel, but I've tried a pre-release from Manjaro and OpenSuse with 4.4 linux kernel version but I've the same problem :(

---

### Post by castrinho8 on 2016-04-03
I've found a workaround in the Arch Forums: [https://bbs.archlinux.org/viewtopic.php?id=210007](https://bbs.archlinux.org/viewtopic.php?id=210007)

Firstable you need a GNU/Linux distribution with a newer kernel than Ubuntu. I've installed Manjaro, but you need the latest version: [16.06 pre-release]("http://manjaro.github.io/download/")
When you arrive at the screen to select your installation, you have to edit the kernel options (clicking "e" letter) and you have to add at the end of the line, the next text and click "enter".

```
"intel_pstate=disable"
```

When you have Manjaro installed, you have to do the same thing always on start menu or add it to the grub configuration ;)

---

