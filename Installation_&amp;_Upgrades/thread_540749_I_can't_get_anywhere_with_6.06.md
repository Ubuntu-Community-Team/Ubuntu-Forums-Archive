---
title: "I can't get anywhere with 6.06"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by alfred_bowman on 2007-09-01
My patience with Windows XP is exhausted.  Something always is going wrong with it.  I have the Canonical installation CD for Dapper Drake and decided to give it a try.  I planned to start by running it from the CD.

I inserted the CD.  Eventually a window opened.  It showed five Open Source applications that could be installed.  I didn't want to do that.  The window also showed:

"Boot from this CD to try Ubuntu without affecting your system." 

 I did so.  Next I got a window showing these five options:

1. Start or install Ubuntu
2. Start Ubuntu in Safe Graphics mode
3. Check CD for defects
4. Memory test
5. Boot from first hard disk

I tried the first three options in succession.  Here is what happened each time:

A window popped up stating: "Loading Linux Kernel."  Next I saw the PC manufacturer's splash screen.  I ended up looking at the above window with its five options.  

I even ran Memory test for about two hours.  (No errors were reported.)  The only untried option was to boot from my first hard drive.  I did so.  I wound up looking at the Windows Desktop.

It would seem that there is something(s) I don't understand about this  Could someone please straighten me out with detailed directions?  I really want to try Ubuntu, but Windows XP has 
consumed my patience with this kind of experience.

[/SIZE]

---

### Post by merlinus on 2007-09-01
Post system specs.  Also, you may want to consider Feisty, which is two versions later than Dapper.

-merlin

---

### Post by mikewhatever on 2007-09-02
The first or the second option is the way to go to get to the desktop. It seems that in your case, something does not work, so it does not load. Post you computer's specs.

---

### Post by alfred_bowman on 2007-09-02
Re: I can't get anyway with 6.06

Specifications:

Presario 2.66 GHz Celeron
768 MB RAM
Intel integrated graphics
Windows XP Home - fully updated

As it happens, I already have downloaded Feisty.  Should I just forget about 6.06 and go with Feisty?

BTW  Windows Explorer reports the size of the Feisty ISO image as 697 MB.  However, the size on disk is 731,799,552 bytes.  Isn't this too large to burn to a CD?

---

### Post by saru411 on 2007-09-02
do you know the version number of this presario? 

memtest is not for installing, its for testing memory settings of course
we need to get you to the desktop screen with either of the first 2 options.
im unsure of why it says its larger than 700MB but if its the normal download it should burn to cd easily.
i have found that the current beta release(feisty in this case) works best for my installs because it has a more recent kernel build. this shouldnt be your problem though. 6.06 should boot fine. i will know more when you give me the version of this presario so i can dig around for more information on installation.
i would also like to point out you should be downloading/installing the 7.04/6.06 LTS as a 32bit o/s(personal computer x86) from here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

don't give up. there are alot of people willing to help you here.

good luck!!!

---

### Post by alfred_bowman on 2007-09-03
Does this info help?

Compaq Presario 061 PJ505AA-ABA SR1210NX NA440 0n41411RE101GIOVA00
System Serial Number: MXK4360BXQ

Board: MICRO-STAR INTERNATIONAL CO., LTD Gamila/Giovani/Neon series 030
Serial Number: 4710090653
Bus Clock: 133 megahertz
BIOS: Phoenix Technologies, LTD 3.15 08/05/2004

---

### Post by Pumalite on 2007-09-03
Your integrated graphics might be the problem. I would go with merlinus advice, but use Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below 'Start Download'

---

### Post by merlinus on 2007-09-03
> 
BTW Windows Explorer reports the size of the Feisty ISO image as 697 MB. However, the size on disk is 731,799,552 bytes. Isn't this too large to burn to a CD?


1MB = 1048576  bytes, so you will have no problem burning the .iso to a 700MB cd.  Just be sure to burn as a disk image, not a data disk, at no more than 4x.

-merlin

---

