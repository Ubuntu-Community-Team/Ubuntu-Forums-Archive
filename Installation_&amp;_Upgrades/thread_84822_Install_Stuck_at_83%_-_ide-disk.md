---
title: "Install Stuck at 83% - ide-disk"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by SiLeNtCovenant on 2005-11-01
Hello all, I just got this Ubuntu CD from my teacher and wanted to install it onto an older computer for my cousin. I formatted the old os and wanted to clean install this one. I've tried the disks on my current computer and they work great. Here's the problem, when I try to install it onto my old computer, it hangs at 83% - *Loading module 'ide-disk' for 'Linux ATA DISK'...*

Anyone know how I can get this to work? I'd really like this comp to run Ubuntu 5.04. I know the hard-drive(ide) works good because I just had WinME running on it a while ago! What's going on?

---

### Post by SiLeNtCovenant on 2005-11-01
Anyone? Please?

EDIT: Oh, did I mention I have Ubuntu v5.04? I dunno if that helps any of you...

---

### Post by SiLeNtCovenant on 2005-11-02
... Guess no one wants to help me ... :???:

---

### Post by duffmckagan on 2005-11-02
Have you tried installing again?

---

### Post by SickTwist on 2005-11-02
Try typing this at the command line (first thing you see when it starts) of the install CD: 

linux noacpi noapic

and press Enter. See if that helps.

If not, there are other hardware options you can disable. Try pressing F2, F3, F4... at the beginning of the install (when you see the Ubuntu logo) and you will see more information. Type the work linux (all lowercase) followed by one or more options:

linux <option1> <option2> ...

It would also help us to help you if you could provide more information about the computer (make, model, processor, etc).

---

### Post by SiLeNtCovenant on 2005-11-02
[QUOTE=SickTwist]Try typing this at the command line (first thing you see when it starts) of the install CD: 

linux noacpi noapic

and press Enter. See if that helps.

If not, there are other hardware options you can disable. Try pressing F2, F3, F4... at the beginning of the install (when you see the Ubuntu logo) and you will see more information. Type the work linux (all lowercase) followed by one or more options:

linux <option1> <option2> ...

It would also help us to help you if you could provide more information about the computer (make, model, processor, etc).[/QUOTE]


Thanks... I'll try mess around with that...
I'm not exactly sure what the pc is, all I know is that it's old...
An old Compaq PC(5140):
Pentium II - 400-500Mhz <-- Not Sure?
32-64MB Ram <-- Same Here
CD-R Drive
Floppy Drive

Dunno what else you would need to know...

EDIT: Oh, I got Ubuntu v5.10 now and it still freezes at the same place: 83%. What's up with that!?

---

### Post by SickTwist on 2005-11-02
Using less than 128 MB (and even that is on the low end) of RAM will make GNOME very s---l---o---w. Be sure to make a swap partition (if you choose automatic partitioning the installer will do it for you) during the installation or you will have problems.

Did you try the options I suggested? Did you try any others?

EDIT: I made a mistake above. Try using these parameters at the start of the installation (when you see the ubuntu logo):

**linux acpi=off noapic nolapic**

If it still freezes, reboot and try this:

**linux failsafe**

---

### Post by ArukiRei on 2005-12-01
I been having this same exact problem trying to install Ubuntu on an old AMD K-6 233MHz computer. I'm not tryng to run Gnome on it, or any graphical interface. I just want to run a low grade personal server. 

I've tried several options to install the server installation to no avail. 

My motherboard is a QDI Titanium IB+
[http://www.qdigrp.com/qdisite/eng/products/tx1bp.htm](http://www.qdigrp.com/qdisite/eng/products/tx1bp.htm)

Any help is appreciated :D

---

### Post by bwog on 2005-12-01
Did you try those bootparameters? What did you try, and why are you posting in a 4 weeks old thread?

I have installed xubuntu today from a normal install disk, I think that is what you want, no Gnome, but a lightweigth desktop. Xubuntu install is in the wiki: [https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29](https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29)

Did you get an error message?

---

### Post by ArukiRei on 2005-12-02
I'm posting in a 4 week old thread becuase it is the same problem I'm getting and it's better to post in a exsiting thread then to make a new one. :P

I've tried multiple boot parameters.

linux acpi=off noapic nolapic

linux failsafe (this only gets up to 73% before it freezes)

I've tried other would seem to help, can't remember them off the top of my head but I will list them in a update as soon as I get off of work. The closest parameter that I thought would help me are the two that have a head,sector,and cylinders in them, but both still froze around 83%. 

Also, I just was to run a server on this, so I don't need to load a desktop environment. 

Any and all help is appreciated :D

---

