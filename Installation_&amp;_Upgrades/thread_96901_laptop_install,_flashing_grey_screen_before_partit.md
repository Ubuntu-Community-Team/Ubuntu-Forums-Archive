---
title: "laptop install, flashing grey screen before partitioner"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by mcewen98 on 2005-11-29
I'm trying to install 5.10 on a celeron 766 compaq laptop, 64mb of ram and I believe 4mb (EDIT: I realized I can change this to 8mb's in the bios) of video ram.  It's a model 1200T.  The lcd was busted, so I removed it and have been using a monitor hooked up to the VGA connector (I'll eventually be getting another display for it and some more memory if everything works out right).  I am also doing the server install and plan on setting up fluxbox or xfce.

The installation works fine right up until before the partitoner.  It says "starting up partitioner", goes to 100%, then before it loads the next screen it goes into this loop of displaying a black screen, a black screen with a grey bar at the bottom, and then a full grey screen, over and over again.

I know my install disk is fine becuase I used it on another machine without any problems.  I looked through the setup parameters and tried using vga=771 but that did not help and the same thing happened.

Any ideas?  Anyone seen this?  I just tried doing a normal full install and it does the same exact thing.

Thanks,

---

### Post by mcewen98 on 2005-11-29
Attempt 2. I did a server install, but removed the wireless network card and inscreased the video memory to 8mb's, and the starting partitioner progress bar hangs at 29%

---

### Post by mcewen98 on 2005-11-29
attempt 3:  set pci=noacpi and disabled the pcmcia card detection.. this results in the partitioner starting screen still going up to 29%, but now it starts dumping memory address's with segmentation fault scrolling accross the screen

---

### Post by mcewen98 on 2005-11-29
attemp 4:  used noapic and nolapic and I got the message "killed" being displayed accross the screen over and over at the same 29% area.

---

### Post by mcewen98 on 2005-11-30
I think I may have figured out my problem in case anyone cares or finds this thread.

My theory is that my problems were being caused by trying to do the installation with only 64mb's of ram, 8 of which were being shared by the video card.  The installation kept failing as you can see by my previous messages around the same point, but with varying error messages depending on the install options that I used...  which I think affected how much memory the installation process was using.  Sometimes I would get a flashing screen, and other times a memory dump or the word killed scrolling down..

I put in a 128mb chip, to make a total of 196 minus the 8mb's for the video card, and the installation so far has gone way beyond where it ever had before.  The base system is almost done installing.  I thought I read that the minimum memory requirement was 32mb's... maybe that's different with breezy, or maybe it's just something funky with this particular laptop sharing it's video memory with the system memory...

---

### Post by Icer on 2005-12-17
[QUOTE=mcewen98]My theory is that my problems were being caused by trying to do the installation with only 64mb's of ram, 8 of which were being shared by the video card.  ...[/QUOTE]

mcewen98,

You are brilliant.  I can confirm that your theory is correct.  After finding your post I changed the video setting on my old HP pavilion n3410 with 64meg of ram 8 of which was dedicated to video.  I switched it to 4mb to the video and got past the killed partitioner error. :razz: 

Kudos!

Icer

---

