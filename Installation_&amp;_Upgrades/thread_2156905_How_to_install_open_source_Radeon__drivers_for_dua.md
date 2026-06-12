---
title: "How to install open source Radeon  drivers for dual boot install?"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by kenandeva on 2013-06-23
Hi.  I am trying to install Ubuntu for the first time.  I am using 12.04 LTS from a DVD I burned.  I am trying to install it for dual booting onto a 64 Bit PC running Windows 8.  When I try to install to *Try Ubuntu Before Installing*, I get a blank screen.  Looking around the forum, I found posts that said I needed to add "nomodeset" to the Grub command.  This worked.  However, I then boot up in command line mode.  Looking at other forum posts, I saw how to check for video error messages.  I did so and saw the error "failed to load module fglrx."  It said the files were not found.  My video card is an AMD Radeon 7570 HD.  From what I've read around the Ubuntu site, those are the proprietary AMD drivers.  However, it seems that [the recommendation is to use the AMD open source drivers.]("https://help.ubuntu.com/community/RadeonDriver")  

So I wanted to know how I can install those open source drivers from the command line.  Is there a way to do it while running under the "try ubuntu without installing" mode, or perhaps I need to actually install ubuntu first?

Thanks for any help!

Ken

---

### Post by ajgreeny on 2013-06-23
I think you mean that you boot to a command line after installing and rebooting your computer, but in live mode the **nomodeset** option gave you a GUI.

If I'm correct you need to use nomodeset from the grub menu you see after powering on the computer.  At the grub menu hit the "E" key to edit the boot option. Using cursor keys go to the line that ends with "quiet splash" and add the word nomodeset so it reads  "quiet splash nomodeset". Now hit Ctrl+X to boot and hopefully you will be in a GUI from which you should be able to install the proprietary fglrx driver that may be needed, or you can add nomodeset to the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` line in /etc/default/grub file, to read ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```and continue to use the open source driver.

---

### Post by kenandeva on 2013-06-23
Live mode CD install with nomodeset put up the GUI, but then when the boot completed, it went back to command line.  That's when I checked for the errors (via command line) and saw the log error msg that said driver files were not there.

---

### Post by kenandeva on 2013-06-23
Here's an update.

Rather than trying to run in *Try without installing* mode, I selected the *Install Ubuntu* option along with the *nomodeset *edit.  This got the GUI install working.  Only problem now is that the install program did not detect that I already had Windows 8 installed.  It seems I have Windows 8 in UEFI which has[ its own special steps required]("https://help.ubuntu.com/community/UEFI").  I'll take a look at that and start a new thread if need be with questions about that.  However, I'll close this thread, the solution seeming to be:  if you have Radeon drivers, *Trying without Installing* just isn't going to work.

---

