---
title: "Ubuntu installed on old computer, but not on new computer, Help!"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by smalltown2001 on 2011-05-25
So I've used Ubuntu off and on for the past year on my Dell Dimension 8300 desktop, and really like it.  So last week I decided to build a new computer and planned on installing Ubuntu as the OS.  Well, I've been working on it all week, and it is making me go CRAZY that it is not working.  Here are the specs:

Old Computer:
Dell Dimension 8300
80 G  Seagate IDE Hard Drive
Installed Ubuntu 9.10 and it works perfectly

New Computer (custom build):
Intel core i5 2500k
Asus P8P67 MB
4 G Memory
SSD 64 GB (also having problems, bios not recognizing it occasionally, but that's another problem)

Tried to take hard drive from Dell computer, plug it in to the new computer, and of course it did not run the OS installed, since it is a different computer, saying " Error: the symbol "grub_getcharwidth" not found    grub rescue>.  So I planned on installing Ubuntu on the same hard drive, but when I get to the point of partitioning the hard drive in installation, it doesn't show any hard drives available.  Gparted doesn't show the 80 G hard drive either.  However, when I look at my computer in the Live Cd, it shows all the file system and files and folders on that hard drive.  I've tried also installing Ubuntu 11.04 32 bit and 64 bit, but it is the same problem.  I've tried also unplugging connectors to see if that would work, as well as changing settings in Bios to see if that works, but to no avail.  Bios does recognize the hard drive.  Does anyone have any suggestions?  Thanks, I really like the look and feel of the new 11.04 Ubuntu, and want to experience that on my new build, but it is proving very difficult.  Thanks in advance.

---

### Post by Quackers on 2011-05-25
Welcome to UF.
Am I correct in thinking that your new motherboard uses sata 3 (6GB p/s)?
I don't think that Linux supports that for the moment. Do some googling on the subject and see if you can find more info.
Fortunately there are other members here who will know more about that than I do and I'm sure they will give further details.

---

### Post by smalltown2001 on 2011-05-25
Well, it does support Sata 6 gbps, but also has 4 plugs for Sata 3 gbps, which i have the DVD and SSD plugged into it.  But the hard drive that I want to install is on the IDE connector.  Also, in the live cd, I tried the disk usage application, and it showed the 80 G hard drive just fine, but still nothing in the Gparted.  Since it is a problem with the new computer, and it is my first build, a few questions:
 
1)  The motherboard came with a DVD with the drivers (i think), but I figured you couldn't install it until you have an OS and drive to install the drivers on, is this correct?
 
2)  Is Ubuntu just not compatible with Sandy Bridge Generation II builds?
 
I planned on using Ubuntu until I could get Windows 7, and then have a dual boot, so I'll find out if the Win 7 will install fine, and maybe then it will narrow it down.  Any other suggestions?

---

### Post by Quackers on 2011-05-25
As far as I know your first point is correct (but I have never had to do that myself).
Again, the last I heard regarding Sandy Bridge was that Linux does not yet support it.

---

