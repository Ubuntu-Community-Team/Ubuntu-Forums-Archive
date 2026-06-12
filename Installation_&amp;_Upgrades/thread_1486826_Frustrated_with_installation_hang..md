---
title: "Frustrated with installation hang."
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by fussnfeathers on 2010-05-18
I really don't know how much info you need.........so here goes.  I've got an old IBM Thinkpad 2647-LU2 (T23) from 2001 or so.  Recently found myself in a position where I could use it again, so I figured I'd replace Win2K with an Ubuntu variant.  Settled on Xubuntu, though I'm right on the edge of specs for that.  Here's my problem.  
 
Trying to boot directly from the CD is a no-go.  It boots, I get the menu, was able to start loading, then it hangs there, never gets past the initial blinking cursor prior to anything installing.  Figured out how to get verbose mode working, so I could see what the heck was going on.  Last line of the text screen is:
 
1.594284 serial 0000:00:03.1: sharing IRQ 11 with 0000:00:03.0 
 
Fine, IRQ sharing can be a backbreaker in Windows, too, so I changed the four assignable IRQ's in the BIOS to four different numbers.  Same thing, but this time the sharing IRQ part changed to 9.  Tried everything I could find, all boot options, all commands, all sorts of combination of cmmands, I can't get past that point.  Even trying to start the demo mode and run off the CD to see where things might be conflicting doesn't work.  
 
FWIW, I downloaded a few other Linux variants, and none of them load.   
 
According to Windows, IRQ 9 (was 11 until I changed it) is used for the modem, the networking, ACPI, sound card, pretty much everything.  I'm assuming this is the problem, now.....is there a way to force Xubuntu to ignore that IRQ for install purposes?  The only workarounds I can find are for ACPI, and I hace yet to find a setting that totally allows for forcing IRQ assignements to different settings while booting.  As of now, I can install Xubuntu from within Windows, but I can't get past the install reboot.  Currently, even with ACPI off in the command line, I'm showing this:
 
9.834097 ACPI: PCI Iterrupt Link LNCK enabled at IRQ 9
9.834154 PCI: setting IRQ 9 as level-triggered
9.834203 serial 0000:00:03.1: PCI INIT A -> Link LNCK -> GSI 9 (level, low -> IRQ 9
 
That's as far as I get.  About the only thing I haven't done is physically disconnect the network/modem card, and try booting that way (since half the IRQ 9 assignments are related to that card).  If I DO do that, and everything finally loads, can I put the network card back in?  I'm sure I'll need to do some editing, but I can't exactly put the card back in while the laptop is powered up.........

---

### Post by utnubuuser on 2010-05-18
try nomedeset at boot:

from another thread:

Google: i915.modeset=0 ubuntu
or i915.modeset=1 ubuntu
or nomodeset ubuntu
and you'll most likely find the solution

in brief:
at the grub menu selection screen (press esc at boot time if you've no grub menu) press e, use arrow keys to scroll to the line that begins with 'kernel', use arrow keys to get to end of line, add "nomodeset" (without quotation marks) after quiet splash, then control+x to boot
if that helps, you can make the change permanent... plenty of how-to's out there...

There is also a forum-sticky regarding known issues with Lucid Lynx, - very helpful

The procedure is slightly different for using kernel parameters from the liveCD, google "nomodeset ubuntu liveCD" or something similar...

Here's a thread:> [http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29]("http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29") for working from the liveCD

---

### Post by oldfred on 2010-05-18
For old systems there are a lot of other options that may help:

[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

Perhaps irqpoll if you are having irq issues?

---

### Post by fussnfeathers on 2010-05-18
Thanks....I'll have a look at both those links. Initially, I wanted to just have Xubuntu, no Windows, and I did try all the common options. I see where I was making a mistake in the first thread, I was getting rid of quiet splash, but I was also getting rid of the -- at the endo of the line, that's probably my problem there. Where I am right now is the installation started from within Windows fine, I already had a seperate partition set up, so I installed to that partition, rebooting to finish the installation stopped at a blinking _ and got no farther. It did modify Boot.ini, so I was able to reboot back into Windows. I'll have to reinstall, most likely. 
 
Once I actually get the darn thing running, I should be fine. I've got enough knowledge of older versions of Linux that I'll at least be able to find my way around initially.
 
*edit*  Did some digging around for a couple of hours, even using the parameter for VESA doesn't get me past that IRQ 9 line.  Nothing does.  I may have to dig for an older distro, either it's a problem with the modem/network (which would make sense, I had an issue with the modem locking Windows up with a driver install), or the fact that this machine doesn't have the graphics chip the majority of other sites I've read have.  I've got an S3 Savage IX, the only workarounds I can find apply to nVidia, ATI, and Intel, the three common ones.  If I boot from the CD, I do get the main run/install menu, and can add/change parameters using F6, so far no joy.  I can install through Windows, install gets to the reboot point, I can use ESC to get into the startup parameters there (which don't match any sites I've looked at, everything I can find applies to problems AFTER a successful install), no joy there, either.  
 
Consider me a n00b here.  There's gotta be something simple I'm missing. Utnubuuser, I searched your suggestions, but.........I'm not even getting that far along in an install.

---

