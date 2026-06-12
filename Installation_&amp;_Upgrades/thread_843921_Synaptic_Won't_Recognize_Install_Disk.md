---
title: "Synaptic Won't Recognize Install Disk?"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Mister Godot on 2008-06-28
Hello!  I'm very new to Ubuntu, or any sort of related OS, so in the past few hours of struggling with this issue, I've learned quite a bit, but it doesn't seem to be enough.

I'm using the Synaptic Package Manager to install the *build essential* package, so I can compile some software code, as told by a tutorial I'm using.

The manager asks me to 
"[I]Please insert the disk labeled:
Xubuntu 7.04_Feisty Fawn_-Release i386 (20070415) in drive /cdrom/[/I]"

I do this, but the message only repeats itself.

The two major things I've attempted have ended up as dead ends.  The first was using an external USB CD-RW drive, which recognized and read the CD just fine.  It put an icon on my desktop which would allow me to access the files within it, but any attempts to make it an active Repository for Synaptic ended in failure.

So, I put the CD back into the laptop's build-in CDROM drive and tried to mount it.  This proved it could read the disk, and that it is also named exactly the way Synaptic wants it to be, as written above.

I wish I knew more about this OS, so I could give a more-detailed write-up, but this is the best I can do.  If there are specific questions from someone willing to help, I'll answer them as best I can.

Thank you for your time!

---

### Post by pytheas22 on 2008-06-28
If you have Internet access on the machine, go to System>Administration>Software Sources and under the "Ubuntu Software" tab, disable the option to use the CD as a repository.  Then it will grab build-essential from the Internet instead.

If you don't have Internet access, what is the output of:
```

cat /etc/apt/sources.list
```

(you can open a terminal under the Applications>Accessories menu)

or at least of all the lines in that file that don't begin with a # (there should be only a few)?

---

### Post by Pumalite on 2008-06-28
Eliminate CD as a source. I don't use Kubuntu, but in Ubuntu:
System>Administration>Software Sources>Click off CD

---

