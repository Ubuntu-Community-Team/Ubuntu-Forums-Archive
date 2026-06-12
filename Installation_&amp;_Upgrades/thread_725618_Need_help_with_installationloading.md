---
title: "Need help with installation/loading"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by grheels on 2008-03-15
Hey folks,
I'm hoping that someone can help me as I am still fairly new to Linux. I am dual-booting Ubuntu/ WinXP and when I try to load Ubuntu Gutsy, it takes about a while to load. When I previously had Feisty on the system, I had no problems with the loading; even when I upgraded to Gutsy- it would load the splash screen within about 20 seconds. I wiped Ubuntu off the HDD and then attempted to reinstall it; now that it's been reinstalled it goes to a black screen and after about 2-3 minutes the splash screen finally appears. I really enjoy using Ubuntu and am trying to get really involved in it so that maybe I could switch completely away from MS, so any help would be greatly appreciated.

---

### Post by Lord Landis on 2008-03-16
When you say that it takes a while to load the splash screen, are you talking about the login screen or the bootsplash that says 'Ubuntu' and has the progress bar?  If you're referring to the former, you probably need to change the framebuffer settings in '/boot/grub/menu.lst'.  Look for the line that contains 'vga=x' and try specifying 791 (1024x768) in place of 'x'.

If you're talking about the bootsplash itself, there may be some other problem.  If that's the case, how exactly did you wipe it from the hard-drive?  Did you run fdisk and re-claim the partition for Windows, or did you do something else?  Also, if you didn't wipe the entire drive, it's possible that there's something in the MBR that's causing the slow-down.

---

