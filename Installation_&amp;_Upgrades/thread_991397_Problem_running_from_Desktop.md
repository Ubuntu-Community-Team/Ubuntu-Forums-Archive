---
title: "Problem running from Desktop"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by xtiano77 on 2008-11-23
I am trying to run the Ubuntu 8.04.1 in my desktop computer; however, when I try, I get the message below after a long wait without any activity.  I purchased the computer in 2005.  It has 1G of ram and a 2GHZ intel processor.  It also has an after market video card which allows me to run two monitors while using windows XP.  I would like to tryit out in that computer before fully installing it.  I tried the same ubuntu version in my laptop and it runs just fine.  I would really appreciate your help with this problem.  Thanks in advance.


Message displayed:


*Preparing restricted drivers...[OK]
*Setting the system clock
*starting basic networking...[OK]
*Starting kernel event manager...[OK]
*Loading hardware drivers...
Segmentation fault
/etc/rcs.d/S10udev: 105 /usr/bin/tput: not found
/etc rcS.d/S10udev: 1: usplash_write: not found
/etc/init.d/rc:317: unsplash_write: not found
/etc/init.d/rc: 317: sed: not found
init: rcS main process (5621) killed by SEGV signal
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (6910) terminated with status 255

---

### Post by lemming465 on 2008-11-25
Run memtest86+ for at least 20 minutes to verify you don't have bad RAM, then run the CD self-test to verify that it reads OK on this PC.  If not, either try burning a new CD or replacing the CD drive.

If you have a dual-monitor setup, you will be much better off with Ubuntu 8.10 than with 8.04.1.

---

### Post by xtiano77 on 2008-11-26
After doing the memtest86+, if the RAM turns out to be the problem, the answer will be replacement before installation or is there a way to correct the problem before purchasing or without having to purchase new ram?

---

### Post by xtiano77 on 2008-11-26
I just performed the memtest86+ and the computer shut down by itself at 30%.  Should I take that to mean that the ram is bad and needs replacement?

---

### Post by lemming465 on 2008-11-26
If the computer is spontaneous powering off, you likely have a power supply problem, or possibly a motherboard problem (bad chinese electrolyte in capacitors, for example).

If the problem is RAM, the first thing to try is reseating it (using antistatic grounding).  Problems with the contacts are more common than problems with the actual chips.

Unfortunately, you aren't going to have much luck installing Ubuntu or anything else until the hardware problems are resolved.

---

### Post by xtiano77 on 2008-11-27
Well, it is pretty much safe to say that I am going to need a new computer.  I saw that Dell is offering some systems with ubuntu already installed.  Are there any draw backs to these pre-loaded systems?  As always, thanks in advance for your help.

---

### Post by lemming465 on 2008-11-28
Sorry about the old hardware.  No, there are no drawbacks to the preinstalled systems.  They won't come with windows licenses, so they aren't suitable for scenarios where you need to dual-boot, but as pure linux boxes they should be fine.

---

### Post by xtiano77 on 2008-11-28
Thanks for your help.  One last question.  I installed Open Office, but it doesn't have a mail program like Outlook.  Is there an equivalent to MS Outlook so I don't have to install that componenet from the MS office suite?

---

### Post by lemming465 on 2008-11-28
Typical GUI mail clients people run are "evolution" (the default Gnome client), "kmail" (the default KDE client), or the ever-popular mozilla "thunderbird".  If you are talking to IMAP4 or POP3 mail servers, use which ever you find most appealing, probably thunderbird.  If you are talking to a Microsoft Exchange server, you may have better luck with evolution.  Terminal emulation fans often choose "mutt".  There are zillions of other clients, but those are the 4 most popular.

If you have to resort to actual MS-outlook, your 3 main options are run an older version under WINE (or the commercially supported cross-over Linux from [www.codeweavers.com](www.codeweavers.com)), or run it remotely via rdesktop, or boot a virtual copy of windows in vmware or virtual box.

---

