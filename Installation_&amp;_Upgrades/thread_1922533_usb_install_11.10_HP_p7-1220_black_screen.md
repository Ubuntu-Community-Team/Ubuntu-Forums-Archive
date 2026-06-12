---
title: "usb install 11.10 HP p7-1220 black screen"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by Gregory Lee on 2012-02-09
I tried to install 11.10 onto a new HP desktop, p7-1220, which has an AMD a8-3820 APU with integrated graphics processor ATI Radeon HD 6550D.  I could get a Grub menu, and I chose the "try" option, but after that the screen was black.  After waiting a while I tried ctl-alt-f1, but still, nothing was visible.
 
More specifically, from Windows 7, I used the program Universl-USB-Installer-1.8.8.0 to load the file ubuntu-11.10-desktop-amd64 on to a usb thumb drive (I tried two different ones), and checked that Windows 7 could read the contents of the thumb drive okay.  One of my thumb drives has a drive light, and when I rebooted, it flickered as I'd expect if the drive was being read and booted from, yet after choosing from the Grub menu, as I said, I see nothing.
 
There was a review last summer on the Phoronics site of an AMD a8-3850 (seems very similar to my a8-3820) with the same graphics controller that I have, and the reviewer found that the free X11 driver in Ubuntu 11.04 did not yet work with this controller, so he had to use AMD's proprietary Catalyst driver for Linux.  So, I'm guessing that's my problem -- that the video driver in 11.10 just doesn't work for my graphics controller.
 
But, what do I do about it?  I'm quite willing to try installing AMD's proprietary driver, but I can't do anything like that when I can't see anything on the screen.  Isn't there a fall back VESA driver that might work?  Can I tell grub somehow to use that?

---

### Post by Gregory Lee on 2012-02-09
By following a different method, I managed to get to a purple screen with choices to try or install.  After choosing "try", though, all I saw was a black screen.  I guess that's progress.
 
This time, I burned a DVD with an image for Ubuntu 12.04, amd64, live or install, and after rebooting, I hit escape to get an HP menu with boot sequence as a menu choice.  On the boot sequence menu, there was one option to boot from the DVD, and under a heading "legacy boot", another choice to boot from the DVD.  I chose the second, arbitrarily, and then got that nice purple formatted menu with the "try" choice on it.  After choosing "try", I heard two periods of activity from the DVD -- Ubuntu getting loaded into memory, I guess.  But then nothing more appeared on the screen.  I tried ctl-alt-f1, with no result.
 
Would there be any point to trying booting the server version of Ubuntu?

---

### Post by Gregory Lee on 2012-02-09
Okay, I seem to be up and running in Ubuntu 12.04 now.  I tried the DVD live/install amd64 boot again and this time used the "nomodeset" option.  It worked, though I haven't actually installed it yet.  I'm in some sort of super vga screen mode, now.  The system setting for the display says I'm using an unknown display, so next, I guess, is to go ahead and install, then see if I find a working driver for my Ati HD 6550D display.

---

### Post by Gregory Lee on 2012-02-09
I can run Ubuntu 12.04, but so far I haven't been able to install it.  Eventually, the install stops with a message "We're sorry, the installer crashed ...", and when I say okay to the question "Do you want to make a bug report ...", I get the message "This problem was already reported in the bug report displayed in the web browser."  However, there is no bug report displayed in the web browser, so far as I know.

Maybe my marking this thread as "[SOLVED]" was premature.

I also tried booting into the current version of Ubuntu, 11.10, using the same steps that got me into 12.04, and I was able to do that, but I wind up with a console command line, and it's not obvious how to proceed from there.

---

### Post by Gregory Lee on 2012-02-10
Well, I do seem to have Ubuntu installed now on my HP p7-1220 Pavilion desktop system.  I'm sorry that the thread title I gave has become inappropriate, since I wound up installing Ubuntu 12.04 instead of 11.10, and I burned it on a DVD instead of using a USB thumb drive.  But I'm not saying you can't install 11.10 on this system or that you can't use a USB drive.  I probably made some mistakes at first.

But here is what worked for me.  I downloaded and burned onto a DVD an ISO file for Ubuntu 12.04, the amd64 version.  When I booted it up, I hit the Esc key to get the HP system menu, chose the boot submenu, and from that under legacy boots, chose the P2 Atapi CDROM item, then hit Enter to boot using that.  When the Grub purple screen came up, with prompts at the bottom for F-keys, I hit F6, chose "nomodeset" on the little subscreen that popped up, then the Esc key.  I chose the "Try Ubuntu ..." entry [footnote *].  After the Desktop come up, I clicked in the Install icon.  Onn the menu that came up I did NOT check the boxes for loading proprietary drivers or for downloading updates during the install [footnote **].

Eventually the install completed successfully.  Using the wheel icon in the upper right corner, I asked to Shutdown, and removed the DVD when it was ejected.

When I rebooted, I got a different style of Grub menu with which I had to use the 'e' key to add the "modeset" option to the end of the boot line.

After this boot, I went to System Settings > Additional Drivers, and asked to activate the AMD proprietary flgrx graphics driver.  I was instructed to reboot, then, and I did (but without adding "nomodeset" to the boot line in Grub).

And that's where I am now.  Much yet to be done, I'm sure.  But it looks nice.

[footnote *] Actually, I didn't choose "Try Ubuntu", I chose "Install Ubuntu" first, but that attempt failed, and I wound up in the desktop, where I probably would have wound up if I had said "Try Ubuntu".

[footnote **] I did, actually, try to include proprietary drivers and do updates during the install, the first time around, but that didn't work, apparently because of a bug causing the install to abort when the proprietary flash driver can't be found.

---

### Post by MAFoElffen on 2012-02-10
> **Gregory Lee said:**
> Well, I do seem to have Ubuntu installed now on my HP p7-1220 Pavilion desktop system.  I'm sorry that the thread title I gave has become inappropriate, since I wound up installing Ubuntu 12.04 instead of 11.10, and I burned it on a DVD instead of using a USB thumb drive.  But I'm not saying you can't install 11.10 on this system or that you can't use a USB drive.  I probably made some mistakes at first.

But here is what worked for me.  I downloaded and burned onto a DVD an ISO file for Ubuntu 12.04, the amd64 version.  When I booted it up, I hit the Esc key to get the HP system menu, chose the boot submenu, and from that under legacy boots, chose the P2 Atapi CDROM item, then hit Enter to boot using that.  When the Grub purple screen came up, with prompts at the bottom for F-keys, I hit F6, chose "nomodeset" on the little subscreen that popped up, then the Esc key.  I chose the "Try Ubuntu ..." entry [footnote *].  After the Desktop come up, I clicked in the Install icon.  Onn the menu that came up I did NOT check the boxes for loading proprietary drivers or for downloading updates during the install [footnote **].

Eventually the install completed successfully.  Using the wheel icon in the upper right corner, I asked to Shutdown, and removed the DVD when it was ejected.

When I rebooted, I got a different style of Grub menu with which I had to use the 'e' key to add the "modeset" option to the end of the boot line.

After this boot, I went to System Settings > Additional Drivers, and asked to activate the AMD proprietary flgrx graphics driver.  I was instructed to reboot, then, and I did (but without adding "nomodeset" to the boot line in Grub).

And that's where I am now.  Much yet to be done, I'm sure.  But it looks nice.

[footnote *] Actually, I didn't choose "Try Ubuntu", I chose "Install Ubuntu" first, but that attempt failed, and I wound up in the desktop, where I probably would have wound up if I had said "Try Ubuntu".

[footnote **] I did, actually, try to include proprietary drivers and do updates during the install, the first time around, but that didn't work, apparently because of a bug causing the install to abort when the proprietary flash driver can't be found.
I've read all your posts where you answered your self and continue on.  Wondering about this last post and trying to translate this...

So it completed a system install ans installed the fglrx driver and all is well now?

---

### Post by grhayes on 2012-03-09
I'm running an A8-3850 as well. The only way I was able to get 11.10 installed was to first install an older version then upgrade to it.

As for 12.04 beta. It seems to run fine off the disk. When you install though and it gets to a point where it is updating or loading new drivers the screen goes black and all control of the system is lost. You are forced to reboot. At least it seems on the right track until it changes drivers or whatever.

If it was me I would make sure the install system works using the drivers or whatever the live version is using then if they want to update the display drivers let them. Make sure it has an auto fall back to the live drivers if they have to reboot for something along that line when the change is going on.

I'd love to see a solution to this.

---

### Post by IslandBill on 2012-06-25
Greg:  thank you for this journal style working out of the issue you were facing, which is one I am facing.  I understood that my 12.04 install was failing because of a video issue -- that was pretty apparent to me due to my years of experience.  It was, however, very nice to see someone put their journey on here for others to follow like a map through the forest.

Nice job, I'll be trying this solution.  It makes perfect sense to me and I'm sure will help me get this installation finished.  :guitar:

---

