---
title: "no LAMP option from server CD boot"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by rleck on 2006-06-12
Greetings
When I boot the server cd, I don't get the splash screen shown on all the tutorials, just a boot prompt. I've double checked, it is the server CD. What command can i type at the prompt for the LAMP install? install LAMP doesn't do it.  :sad: 

Many thanks
R

---

### Post by rleck on 2006-06-15
It's me again. I have tried the self same CD in another machine, a P111, and the splash with all the appropriate choices is there. Could it be a hardware issue with my older P11 that prevents the splash menu? The old P111 does meet the minimum requirements....

Cheers

---

### Post by nick1 on 2006-06-19
I'm encountering the same situation.  I'm trying to install Ubuntu 6.06 server edition on a Pentium 450MHz with 256MB of RAM.  I don't see the splash screen either.  How do I access the LAMP install option?

Thank you for your time,

Nick

---

### Post by nick1 on 2006-06-21
Update:

You may want to try using a different video card.  In this specific system I had a Diamond Fire 1k Pro AGP ATX 8M T3, the date on the card was 1997.  I removed the video card and popped in an ATI IIC(?) card that I had laying around.  I booted from the Ubuntu 6.06 server cd and can now see the GUI splash screen with the option to install a LAMP server.
I don't like the fact that I had to replace the video card.  There should be a command to issue that installs the LAMP server if the GUI splash screen is not displayed.  Does anyone know what that command is?

Nick

---

### Post by peaceful_dragon on 2006-11-24
I seem to be getting the same problem... In this case I'm trying to install onto a Parallels Workstation VM in Mac OS X.

[http://www.ubuntuforums.org/showthread.php?t=305984](http://www.ubuntuforums.org/showthread.php?t=305984)

---

### Post by rleck on 2006-11-25
Shame on me for never updating my own thread. I threw an old PCI video card into the PII machine, turning off the on-board video in bios. Hey Presto! A proper boot splach with the menu. The install then progressed painlessly. I removed the video card after the install and the server has chugged merrily since then. This has since happened and been easily resolved on a different machine trying to install Edgy.

Peaceful_Dragon: While I am no expert in VM or Mac OSX, perhaps its a case of the installer not seeing the video hardware properly, virtually or otherwise, at install time?

---

