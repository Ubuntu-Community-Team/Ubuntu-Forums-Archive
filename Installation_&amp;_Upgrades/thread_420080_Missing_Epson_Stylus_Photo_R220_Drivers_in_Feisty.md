---
title: "Missing Epson Stylus Photo R220 Drivers in Feisty"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Zebidiah on 2007-04-23
I've just upgraded to Feisty (Kubuntu) from Edgy.  When I went to install my printer the Epson drivers for the printer (Epson Stylus Photo R220) were not there as they were in Edgy. :confused: 

Can someone please confirm that the drivers are indeed missing or maybe there is someone wrong with my install media which is the kubuntu-7.04-desktop-amd64 ISO.  Are the drivers available?  If so, how did you upgrade and with what disk?

I am just trying to determine what the best course of action is.  Upgrade from Edgy to Feisty via the upgrade manager or install the Ubuntu disk and then install the KDE desktop from there or perhaps use the Kubuntu alternative ISO.   Any thoughts?  TIA.

---

### Post by mmxbass on 2007-04-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/108435](https://bugs.launchpad.net/ubuntu/+bug/108435) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This bug and similar are already known at [https://bugs.launchpad.net/ubuntu/+bug/108435](https://bugs.launchpad.net/ubuntu/+bug/108435) and [http://ubuntuforums.org/showthread.php?t=412990](http://ubuntuforums.org/showthread.php?t=412990).

It's not just you. Many MANY Epson users are really fuming right now. Somebody working on Feisty screwed up BIG.

---

### Post by Zebidiah on 2007-04-23
Thanks for the reply.  I've been searching to see if it was a common problem but I was unable to find anything.  I guess I was looking in the wrong places.  I figured that it may have had something to do with 32\64 bit drivers since I was unable to find anything.  I've went back to Feisty as my life is being made uncomfortable by others who need the printer.

I'll check from time to time on a spare drive to see if they are replaced by an update.

---

### Post by mmxbass on 2007-04-23
> **Zebidiah said:**
> Thanks for the reply.  I've been searching to see if it was a common problem but I was unable to find anything.  I guess I was looking in the wrong places.  I figured that it may have had something to do with 32\64 bit drivers since I was unable to find anything.  I've went back to Feisty as my life is being made uncomfortable by others who need the printer.

I'll check from time to time on a spare drive to see if they are replaced by an update.If you don't mind, could you post your experience in the aforementioned bug report? The more people we get complaining, the quicker it will get fixed.

---

### Post by Zebidiah on 2007-04-24
I've added my comments to the bug description at launchpad.  Hope this helps.

---

### Post by mmxbass on 2007-04-24
> **Zebidiah said:**
> I've added my comments to the bug description at launchpad.  Hope this helps.It always helps. The more people report the bug, the more information the developers have to work with, the faster the bug gets fixed, the sooner we can print. I'm expecting a small wait since obviously Feisty was just released and they must be overwhelmed with bug reports and even though this problem is major to us (we can't print), in the grand scheme of the operating system, it's relatively back-burner. Presumably stuff like system instabilities get handled before peripheral support. I think we can all agree that we would rather they take care of someone's malfunctioning video driver (the "nvidia-glx enable" bug) before they look at our printers.

---

### Post by Zebidiah on 2007-04-25
I can certainly agree that system instability bugs should be looked at first as this affects everyone.  I don't really need a printer (for myself) very much but others in the household do.  I've went back to Edgy which I am more than happy with except that Amarok no longer works.  I think the Feisty version upgraded some config file which is incompatible with the Edgy version.  Just to check I renamed the amarok folder after which amarok would successfully launch.

I'm in the process of installing Edgy now and will try the upgrade tonight if I have time.

---

### Post by mmxbass on 2007-04-26
Once they get to this, it wont take them long to fix I'm guessing. It seems like it's just going to be a matter of repackaging the driver and pushing the update.

---

### Post by Zebidiah on 2007-04-28
I agree.  Just tried an upgrade from Edgy to Feisty.  The upgrade ran okay until it tried to clean up then crashed.  The OS worked fine until I rebooted and there was a problem with the X Server when booting into KDE.

I wasn't expecting it to work as I had some 3rd party repositories installed.  It turned them off during the upgrade but there still must have been something wrong.  I'm content just to wait now.

---

### Post by Spike-X on 2007-04-28
That's odd, my install of Feisty has the Epson Stylus Photo R220 driver. I just now installed it and used it to print a test page on my Epston Stylus Photo R230 (which doesn't have an available driver - Epson recommend using the R220 driver for the R230, which worked fine under Edgy).

---

### Post by bkremers on 2007-04-29
I have a Epson Stylus Photo R300 and I had the same problem. I've installed through adept manager  the "foomatic-db-gutenprint" package and all the missing drivers were there.
Hope this helps for you as well.

---

### Post by mmxbass on 2007-04-29
> **bkremers said:**
> I have a Epson Stylus Photo R300 and I had the same problem. I've installed through adept manager  the "foomatic-db-gutenprint" package and all the missing drivers were there.
Hope this helps for you as well.This works for the CX series as well. This looks to be the simplest solution for the problem as well.

---

### Post by westlye on 2007-06-28
Hello,
when I upgraded my Kubuntu to Feisty Fawn I lost my Epson Inkjet Photo R220 driver.
Surfing the web i found that:
[http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html)
has drivers, I downloaded the RPM version for Debian, then I used the utility alien
to create a .deb installation file.
Alien is a program that converts between the rpm, dpkg, stampede slp, and slackware tgz file formats to .deb and can be downloaded from: [http://kitenet.net/~joey/code/alien/](http://kitenet.net/~joey/code/alien/)

then a at a console type the command: sudo dpkg -i filename.deb 
Viola, now the printer (among other missing Epson printers) showed up in the printer installation guide.

Hope this will help others that have problem after upgrade.
Regards//LW

---

