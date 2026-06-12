---
title: "Cannot CORRECTLY mount CDROM during installer process"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by StrangeWill on 2008-10-05
So I ended up using the alternative Ubuntu install for my last issue, everything seems to work okay, I can detect the CDROM, I set up my partitions, then it goes to copy the OS over...

> 
Cannot install base system.
The installer cannot figure out how to install the base system. No installable CD-ROM was found and no valid mirror was configured.


Again, I'm on a Sony Vaio laptop (PCG-632L), DVD Rom is on the docking station. I'm figuring the docking station may have something to do with it, it gives me the option to load custom modules, but I don't have any to load (says to put them on a floppy disk), and the only ones I can select from are "CDROM" which causes the error. :(

---

### Post by StrangeWill on 2008-10-05
Nothing at all?

Edit: I'm checking CDROM integrity, it's working so far... geez this thing is finicky.

Edit2: Still no go, could be the hard drive, too bad this is an issue no one has confirmed what the problem really can be.

---

### Post by StrangeWill on 2008-10-06
I know that Fedora allowed you to do a web install, is there a web installer for Ubuntu? Maybe I can try this...

---

### Post by katiesmily on 2008-10-06
Yes i can not connect correctly cdrom during installation why iam facing this problem can any body help me.
__________________________________

[neu verlieben](http://www.singltereff-singleboerse.de/liebe.html) 
[cowboy boots](http://www.timsboots.com)

---

### Post by StrangeWill on 2008-10-06
Well I can open the shell and read the CDROM's contents, seems the installer is messed up somehow, what an annoyance!

Edit:
Score, unmounted the CDROM, force ejected it (for some reason the installer locks it from being ejected), re-inserted it, remounted, and it's working!

Bugger that was annoying.


Edit2:
Now I'm stuck at 71% "configuring APT sources", apparently this can be caused by not having enough RAM, which IMHO is complete BS, I can install and run Windows on this machine, why can't I install Ubuntu?

386mb of RAM, not a huge amount, but comeon, WINDOWS. Guess I get to wait another day or two as I figure out how to get RAM into this damn thing and buy some.

Edit3:
Sony says that 386mb is the max this little guy can handle, so I guess I'm going with the low-memory desktop Ubuntu. gah I hope I don't lose functionality/customization of the GUI.

---

