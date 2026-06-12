---
title: "CD won't mount!"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by Maww16 on 2007-12-08
Please help me!  I have tried EVERYTHING.  I have roamed every forum I could get my hands on.  Spent countless hours on this.  My CDrom drive won't mount AT ALL.  I can open it...put a CD or DVD in...the icon in "Computer" comes up but when I try to open it it says it cannot mount.  And I have made changes according to each forum and I get various effects.  Sometimes it says can't find blahblahblah...other times it says its not a block device.  I went roaming in my files and noticed I dont HAVE a device in /dev that comes anywhere near anything these others had.  I remember yesterday reading that it might be becuase my kernel isn't compiled to see my drive correctly.  I believe I need to recompile my kernel.

For the love of all things good and holy...Could someone please help me step-by-step on how to recompile my kernel to get my CD drive working.  

If it helps any...when I did the live CD to install, it recognized my drive in computer as a CD-RW/DVD+RW Drive.  But after installation it only sees it as a CD drive.

---

### Post by Pumalite on 2007-12-08
What BIOS do you have? How do you have CD setup in BIOS?

---

### Post by Maww16 on 2007-12-08
I don't know what bios i have...how do you check?  I'm sorry i'm still new to some of this stuff.

My cd is set to boot before my harddrive.  Don't tell me to set it after...already tried that.  didnt work.

also...i'm running ubuntu 7.10.  I have a laptop as well and the CD/DVD i'm using is a pioneer...which i have checked the list...its not a proprietary drive.

---

### Post by Pumalite on 2007-12-08
Give me the model and number of your laptop.

---

### Post by Maww16 on 2007-12-08
Honestly it's a custom built laptop...I bought it from 800hightech.com.  The name on the case is Style-Note and the model on the bottom of the laptop says M57U.

---

### Post by Pumalite on 2007-12-08
What are your specs?. Memory, graphics, processor.

---

### Post by Maww16 on 2007-12-08
Intel pentium 2 Dual Core
2g RAM
7950 GTX nvidia 512mb
I only know the maker of my CD/DVD burner.  It's Pioneer.  I don't know how to find out in linux.

---

### Post by Pumalite on 2007-12-08
When you boot your computer you can hit 'Del' or 'Tab' or Esc' (consult your manual) to get into BIOS>IDE Cofiguration>Make sure CD is set to AHCI or 'Auto'. Also CD should be 2nd Master in your computer.

---

