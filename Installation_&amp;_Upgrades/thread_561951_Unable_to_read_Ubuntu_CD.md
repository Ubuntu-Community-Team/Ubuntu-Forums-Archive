---
title: "Unable to read Ubuntu CD"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by coryandtrevor on 2007-09-28
I got the Ubuntu installation sent to me from a redistrubitor. its the 7.04 cd with the cd sleeve which has 4 people on the cover. But it doesnt seam to be readable in my Desktop PC. 

I tested it in my laptop and it seams to work fine and when put in will load up the Ubuntu thingy. But on my Desktop it doesnt do anything and when I try and explore the CD it seams to think its blank or empty and doesnt do anything or show any files - doesnt say insert a cd tho

The DVD/CD drive is a Lite-on - DVDDRW - SOHW-1673S thats what its says when i right click > properties on the drive. The drive is working though as when i put a DVD in it reads that fine aswell as a normal CD (the open office cd)

Im running windows XP. I have tried cleaning the cd. 

Any ideas,

---

### Post by pyrodrake on 2007-09-28
Generally, and by default, the CD is unable to be read in windows.  I think this is due to the file system differences.  If you have the computer set up to boot from CD, it should still boot/install fine.  I'm not sure if it works with CDs, but you may want to try [Ext2 IFS for Windows.]("http://www.fs-driver.org/")  It works for me for reading the Ubuntu-formatted partition in Windows.  Not sure if it will work with CD's though...  Good luck, and hope this helps!  :)

---

### Post by Biggus on 2007-09-28
Dude, I'm guessing that your Desktop PC isn't set to read from the CD (or DVD) drive when you switch your PC on, but that your laptop is.

What happens when you switch on your PC is that the PC will look to see if it can find some sort of drive with an Operating System on it. This could be on, for example, a hard drive, a CD, or a USB memory stick.

If you have more than one of these devices plugged in when you switch your PC on, it will go through them in the order in which they are listed in your 'BIOS settings'.

A typical list may look like :

1:Hard Drive
2: CD-ROM
3:USB

In this case, the PC would look for an OS on the hard drive first, if it doesn't find one, it will look on the CD-ROM, and if there isn't one there, then the USB drive.

What you need to do is to change your BIOS settings so that your PC looks for the CD-ROM drive before it looks at the hard drive. (It's probably called 'boot setup' or something in your BIOS)

You normally access your BIOS settings by pressing a button on your keyboard just after you switch your PC on. (On my Dell, it's the F12 key, but your PC may be different)

---

