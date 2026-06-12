---
title: "LiveCD Black Screen (No signal to monitor)"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by mbelly on 2006-06-27
Hello fellow Ubuntu users,

I made the decision this past weekend to ditch Windows and finally use Linux as my primary OS, instead of under a virtual machine.  I tried both SuSe 10.1, and Ubuntu, and have had a little troubles getting each installed.  This message will focus on my attempt with the Ubuntu install.

When I put the Ubuntu CD into the drive and reboot my machine, the live cd goes through it's boot sequence, allows me to select LiveCD/Installation, and brings up the splash screen of Ubuntu while it loads its modules, etc.  Eventually it seems to finish this piece, but the screen goes black, and the monitor goes to sleep with a "No Signal" message. ](*,) 

This is likely a video issue, but I tried selecting a resolution at the startup screen that should work with my monitor / video card, and it still did the same thing.  I also tried safe video mode, and that still ended with a black screen.  I have also tried ctrl+alt+f1-f6 and ctrl+alt+backspace to no avail. 

My video card is an ATI Radeon X800 PCI connected to an Asus A8V motherboard with an AMD64 processor.

Does anyone else know how to get past this issue?  I'd like to get Ubuntu installed, but that is pretty difficult if I can't even boot the CD. :)  I've searched the forums a little, but most of the threads I see are for nVidia cards, or post-install issues.  My issue starts with the LiveCD. :)

Thank you in advance for any help,
~Matt

---

### Post by th3james on 2006-06-27
Have you tried the 'Alternate' install, it doesn't use a GUI

---

### Post by mbelly on 2006-06-27
That partially worked, now I have installed the system, but it does the same thing upon booting the installed system.  Any suggestions?

Thanks,
~Matt

[QUOTE=th3james]Have you tried the 'Alternate' install, it doesn't use a GUI[/QUOTE]

---

### Post by ThrashJazzAssassin on 2006-06-28
I've got exactly the same problem with a GeForce FX5200 and a fairly old LCD monitor with a native resolution of 1280x1024@60hz.

Very strange. I assume the refresh rate is too high so my monitor is switching off. I've never had this problem before and tens of live CD's have been tried on this hardware over the years.

---

### Post by ushineko on 2006-06-28
I had this problem with an x700pro, the problem is that the pcie x-series ATI cards do not work with any of the supplied drivers out of the box. You would have same problem on fedora core, or other distros, with similar hardware and kernel. The problem has been widely reported.

You have to install in text mode first, then get the system up to a terminal prompt and install the proprietary fglrx driver for the ATI card. After that point X should work. There's a bunch of guides that will clarify this. Here's one:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

hope this helps...

---

### Post by mbelly on 2006-06-29
Hmm, I have a normal AGP card, but I will still give this a shot after we move into the new apartment today.   The computer is all packed up at the moment.  Thank you. :)

~Matt

---

### Post by dbw on 2006-07-15
I had this exact same problem.  When I looked at my /etc/X11/xorg.conf file I saw three bizarre entries having to do w/ wacom tablet pc crap.  I do not have this functionality, so I commented those lines out in my xorg.conf, and now everything rocks beautifully.

---

