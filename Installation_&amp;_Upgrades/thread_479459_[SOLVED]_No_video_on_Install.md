---
title: "[SOLVED] No video on Install"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by tbrminsanity on 2007-06-20
I just bought some new hardware (Core2Duo, Radeon x1300, Gigabyte motherboard, and 2GB RAM) and I went to reinstall Unbuntu 7.04.  When I load the LiveCD the screen kicks out as it logs in.  I know it is still working as I can hear the system sound and the computer is still active.  I don't have a VGA monitor hanging around so that may be the problem.  My current monitor is a Sony SDM-HS95/B family with the digital in.  Is there someway (short of asking my neighbor for his monitor for a few hours) to get video to the screen through the LiveCD so I can install Ubuntu again.  I currently have WinXP loaded but I hate it with such a passion (stupid GenWin Disadvantage crap).

There is still a couple of things I need to try though.  The motherboard does offer a graphics booster that may help out, and I know I can install Suse as well (the Live CD runs)(but I prefer Ubuntu).

---

### Post by taurus on 2007-06-20
Try using the alternate CD to install it.

---

### Post by mopey on 2007-06-20
> **tbrminsanity said:**
> I just bought some new hardware (Core2Duo, Radeon x1300, Gigabyte motherboard, and 2GB RAM) and I went to reinstall Unbuntu 7.04.  When I load the LiveCD the screen kicks out as it logs in.  I know it is still working as I can hear the system sound and the computer is still active.  I don't have a VGA monitor hanging around so that may be the problem.  My current monitor is a Sony SDM-HS95/B family with the digital in.  Is there someway (short of asking my neighbor for his monitor for a few hours) to get video to the screen through the LiveCD so I can install Ubuntu again.  I currently have WinXP loaded but I hate it with such a passion (stupid GenWin Disadvantage crap).

There is still a couple of things I need to try though.  The motherboard does offer a graphics booster that may help out, and I know I can install Suse as well (the Live CD runs)(but I prefer Ubuntu).

It's probably your video card and not your monitor.   You could try taking out the video card and running from your built in output, if you have any.  

If you just need a terminal try CTRL+ALT+F1 and you can do basic troubleshooting there.

Also, are you using the latest version of Ubuntu?  I've had problems with new hardware if I don't have the newest kernels before.

---

### Post by tbrminsanity on 2007-06-20
Thanks I will give those a try

---

### Post by tbrminsanity on 2007-06-23
I still had trouble with the video even after I installed Ubuntu, but when I pressed Ctrl+Alt+F7 it worked instantly.  I instantly installed the ATI drivers and I haven't had a problem since.  Thanks for everyone's help.

---

