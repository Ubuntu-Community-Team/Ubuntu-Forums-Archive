---
title: "Xubuntu didn't install X ?!?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by PaganHippie on 2007-10-25
I'm trying to shoehorn Xubuntu 6.06.1 'Dapper' into an old laptop computer with 2.1GB of HDD and 64MB of RAM, using the 'Alternate' CD.  The system requirements stated on the Xubuntu website indicate that this should be possible.  Everything seemed fine during the install, no error messages of any kind (although the installer did alert me that I was in 'low memory mode'), and the system dutifully rebooted -- to Runlevel 2.   All things command-line are working fine, and I can even browse the Internet using *links*.

Snooping about the file system, it appears that neither Xfce nor even the X Window system got installed at all.  Is this an artifact of having installed in low memory mode?  Is it possible that the installer didn't recognise my video hardware (Cirrus Logic GD7548 chipset)?  Will *apt-get*ting *xubuntu-desktop* fix the problem (or possibly compound it)?

Yeh, I know, this old system will probably never be terribly useful, but that's not the point.  Mucking about with old computers is my hobby, and I'd just like to understand what went wrong and whether it can be fixed.  In case anyone cares or it's relevant, the machine is an Olivetti Echos 200SM with a German-layout keyboard.  The maximum display resolution appears to be 800x600 in 16-bit mode.

Good night and thank you for your attention.

---

### Post by aysiu on 2007-10-26
There are a couple of possibilities here:
2.1 GB isn't big enough space, but you probably would have received some  kind of error message.
You accidentally selected the *Install a Command-Line System* option from the Alternate CD, but it sounds as if you know what you're doing.

Bottom line: I don't know what happened. It's not too late to install Xubuntu, though: ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by PaganHippie on 2007-10-26
Thanks, I'll try that.  I do have some concern, based on some googling, that my video chip may no longer be supported by Xorg, but I guess I'll find out, won't I.  ;-)

---

### Post by PaganHippie on 2007-10-26
Almost worked.  Everything's in there now, but X won't start.  I'm guessing I'll need to reconfigure X by hand, probably reduce either resolution or bit depth.  Unfortunately, no time right now; hopefully I can take a swing at it this evening.

Thanks again for the feedback.

---

### Post by PaganHippie on 2007-10-26
Tweaking xorg.conf by hand worked.  I changed the default bit depth from 24 to 16 and removed all references to "1024x768" resolution, rebooted, and am now looking at the Xfce desktop.  :-)

Thank you again for your help!

---

### Post by PaganHippie on 2007-11-06
ADDENDUM:

FWIW, I encountered the same lack of X/Xfce just now after installing from the Xubuntu 6.06.1 PPC Alternate CD onto an 'Old World' Power Mac G3 beige with 64MB of RAM.  Apparently 'Low Memory Mode' installs a command-line-only system, regardless of the architecture.  As noted above, though, it is still possible to install the desktop.

---

