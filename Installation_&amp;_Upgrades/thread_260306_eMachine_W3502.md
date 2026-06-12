---
title: "eMachine W3502"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by joegumbo on 2006-09-18
Hi,

     I ust purchased an eMachine Model W3502 chipset Intel D101GCC graphics by ATI Radeon XPress 200 Monitor is KDS XF-7s.  This seems to be the only Linux that Ubuntu 6.06 seems to be the only Linux that will go on this reasonable well.  SuSE freezes, Xandros just hangs, Mepis has no sound and the graphics are weird.  

     Ubuntu 6.06 has sound, but the graphics are overly blown up.  I tried changing the screen resolution, but the only one on the drop down menu is 640x480.  

     I then tried the  "sudo dpkg-reconfigure xserver-xorg" command.  I went through the wizard, but when I come back to System>Screen resolution, I still only have the choice of 640x480.

     How do I change the resolution?   I tried to install, but all the buttons are off the screen.

Thanks,
-Joe G

---

### Post by zxee on 2006-09-19
After running the dpkg-reconfigure script you may need to restart the xserver i.e Alt+Ctrl+Backspace keys. If that doesn't work take a look at your /etc/X11/xorg.conf file or post it.

---

### Post by joegumbo on 2006-09-19
Hi ZXEE!

   Thank you for the help, but I've run into another issue. Ubuntu cannot reboot.  It just hangs and I have to force a hard shutdown.  I think that this system might still be too new for Linux.  I've been checking around the various Linux fora and I keep reading either nothing about the W3502 or work arounds that involve replacing hardware.  I really don't want to void my warranty by altering the hardware.  I'll just use Windows for a while, even if I do have to suffer the indignity of being accosted by "Clippy" as I work.  Edgy Eft should be ready in a few months.  I also read today the Fedora CORE 6 is on the way. 

     Mepis' graphics are a little weird on this machine and there's no sound.  Knoppix5.01 seemed to work perfectly, but wouldn't reboot after "Shut down sequence".  It also refused to install on my HD because it couldn't understand my filesystem. 

Thanks,
-Joe

---

