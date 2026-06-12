---
title: "Ubuntu installed, how do I boot to it?"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by GreenLantern33 on 2006-07-05
I completely wiped out my computer the other day, and reinstalled windows xp.  I thought that while I was doing this I would go ahead and install Ubuntu.  What a good oppurtunity right?

I read up on a few tutorials, and got a plan together.  However at the end of the installation all the tutorials say that it will ask you if you want install grub.  (so that I can dual boot Linux and Windows)  This never happened for me.

So what I have now is a machine with windows and linux, but I can't boot to linux.  How can I fix this?  How can I make a boot disk so that I can boot to linux?

Thanks,
GL

---

### Post by Sef on 2006-07-05
It is unclear which you installed first, but check out this site:  

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by GreenLantern33 on 2006-07-05
I installed Windows then Ubuntu, just like all the tutorials said.

I think that link you gave me is what I have been looking for.  

I'll give it a shot.  Thanks!

---

### Post by GreenLantern33 on 2006-07-05
See this is what I am concerned about.  This was taken from the [graphical install guide]("https://help.ubuntu.com/community/GraphicalInstall") that I followed:

> When your computer reboots it will load Ubuntu if it is the only operating system on your computer or give you a choice between the installed operating systems if you have more than just Ubuntu.

Why didn't that happen for me?  Instead it just boots straight to Windows like Linux is not even there.

---

### Post by richardq on 2006-07-05
I'm having troubles of my own trying to dual boot Dapper and XP but I haven't managed to get Dapper to install fully yet. Anyway, one of the better guides to dual-booting Ubuntu/XP that I've found is at:

[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/]("http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/")


When I was running Breezy/XP (back before I got stuck in this Dapper nightmare) I had the same problem you're having and I eventually found that I had to use XP's bootloader (called NTLOADR) which would then give me a choice of XP or linux. Choosing linux would *then *bring up GRUB which would let me select which kernel to run. It worked fine for me for months, but then of course I had to tinker with Dapper ;).

The link above describes how to use NTLOADR to do a dual boot as well. Good luck.

---

