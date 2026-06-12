---
title: "Neither Ubuntu Installer or partition magic will work"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by CoriolisSTORM on 2007-06-28
Alright gents, I have decided to give Ubuntu another try (I promise I'll make it this time!  My wireless card WUSB54G V4 is finally supposed to work out of the box!) and decided to try to reinstall Ubuntu again.  

I have 6.06.1 and got to the desktop and such fine, checked, and all my hardware was recognized (wireless card freezes the live CD when started though, its a known problem), but anyway, I opened the installer with no 

issues, got to the Partition section, and selected the option to resize HDA1 and place a 30 GB portion of it for Linux.  However, the hard disk spun up, didn't go to any other screens or anything and gave me an error about

 "Unable to create enough space."  Or something along those lines, no error codes or anything though.  I tried with Partition Magic as well before I booted Ubuntu, as its what I've always used in the past.  Well, it rebooted

 and gave me an error too (sorry, dont have the number) but suffice to say it wouldn't repartition my disc eithre.  I have:  AMD Athlon XP 2800+, 512 MB PC 2700 RAM, 64 MB integrated Geforce 4 MX, 120 GB HDD with 2

 partitons, a C&D D is a locked recovery partition that shipped with the PC and is 5.5GBs, C is a "106 GB" partition with 59.8 GBs of free space, so I have enough space, I can not determine what is causing the error.  

Do you all have any suggestions?  edit:  My apologies, I forgot two important facts:  My partition I am trying to get the space from is NTFS, and my recovery partition is FAT32.

---

### Post by CoriolisSTORM on 2007-06-29
bump, any suggestions?

---

### Post by poohbear1616 on 2007-06-29
I use a Gparted live disk for such disk changes and it is wonderful.
You never mentioned if you had xp or vista, you have to go about it different for each.

But anyways get a gparted disk.

---

### Post by costa_g on 2007-06-29
Firstly can you please try reading through your posts before submitting and maybe try using some line spacing as your post was difficult to read and may be the reason you have not received any responses yet.

Secondly, what happens when you try partitioning on install?

Also what version of Windows are you running?

---

### Post by CoriolisSTORM on 2007-06-29
Sorry, I use 1280x1024, so the window is much bigger for me and much easier to read.  Anyway,

it is XP and as far as the installer goes, it loads, I get to the Partitioning step and it gives me an error saying

"Unable to create enough free space."  This is totally wrong, I have 59.8 GBs of free space to work with.

I will try Gparted, maybe it will work better.  Can it work with NTFS?

---

### Post by poohbear1616 on 2007-06-29
Have you run the defrag in xp?
If not run it about 3 times (from what I've read). Can't say from experience since I've never used xp.

---

### Post by CoriolisSTORM on 2007-06-30
Update:  The LiveCD gave me an error about some clusters not matching up.

Apparently my hard disk is full of errors.  I have ran chckdsk and have hopefully fixed them all.  

Now I am off to try GParted again.

Update:  Gparted gives me an error about a cluster being referenced multiple times, and P

artition Magic quits with the error  698, and tells me "Too many errors to continue."  

I've installed Ubuntu fine in the past, I'm not sure what has caused this.

---

### Post by poohbear1616 on 2007-06-30
How old is the hard drive?

Hmmm!!.........Have you backed up all your important goodies?
If not, do so soon.  
My guestimation is either a virus that has segmented the drive (there are some capable of doing so),
or the drive is getting ready to give out. I've had two drives start getting corrupted segments
right before giving out.

---

### Post by CoriolisSTORM on 2007-06-30
I dont really know how old it is, its an HP Pavilion A320N.  Dont have anything "important" on it really, just a few

 pictures I'd like to keep.  I'll take care of that now along with my Documents.  Other than that, it will not be a 

problem.  I was thinking about investing in an external drive, but I might need an internal one now.  I read 

somewhere that Partition Magic does some crap where it tries to increase your hard disk's performance by doing

 something with clusters and such, could this have caused the errors?  My biggest problem right now is HP is too

 cheap to do Recovery CDs anymore, and as such ship their PCs with a recovery partition with a program 

designed to make the CDs.  However, my program has never worked correctly, so if it craps out, I'm SOL as far 

as XP goes.  Like the user name and avatar BTW.

edit:  Found it in the user guide:  

Ability to resize clusters on NTFS partitions  wait, it says when upgrading from FAT32, maybe not...

---

### Post by poohbear1616 on 2007-06-30
Here is a link to your system specs:

[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00039102&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00039102&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN")

sept/03 release date.

You might try running scandisk and put it on the thorough setting and see if it can correct it.
The thorough usually takes a while so have something else to do while it is running.

Don't know about partition magic, I have never used it but I suppose it is possible
it changed the sector sizes or something to that effect. Kind of crappy of it if it did.

---

