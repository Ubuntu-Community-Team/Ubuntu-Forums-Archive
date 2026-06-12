---
title: "How to boot from Live CD if already running 9.04"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by michaelvoss on 2009-12-26
OK - I guess I'm just an idiot, but here's my question:

I've been running 9.04 for months now. I decided to do a fresh install to 9.10 today. 

I've downloaded and burned the ISO and the live CD works because I can get it to open and give me the options about Demo & Full Installation, etc.

The problem is that when I restart the computer with the live CD in it, 9.04 just boots up every time as normal.

I even ran the program on the CD that supposedly configures your computer to boot from CD.

I guess there's a CHANCE the CD is burned incorrectly. 

I've searched, but basically all of the info out there is about how to get WINDOWS to boot from CD and not an existing Ubuntu install.

---

### Post by taurus on 2009-12-26
You probably need to tell the BIOS to boot from the CD/DVD first instead of the harddrive.  Either go into the BIOS and change the order of boot or probably press F12 to bring up boot device screen.  Then, tell it to boot from the CD/DVD.

---

### Post by avtolle on 2009-12-26
Is your BIOS set to boot first from the CD? Check this first. When the computer first starts, there are "fleeting messages" that appear such as Change Boot Order (or words to that effect) followed by the key to press, e.g., F9 on my Compaq F750US laptop, F12 on my daughter's Dell laptop and a friend's Dell desktop; there are others, depending upon the maker. Pressing the correct key will give a menu which lists the options. Good luck.

---

### Post by ajgreeny on 2009-12-26
There is no such thing as a program on the CD that configures your computer to boot from CD, or if there is, it's a new one to me.  You must change the boot order in the BIOS, as others have said.

---

### Post by PFree on 2009-12-26
My wife's eMachine/desktop comes up with an option to boot from CD on system start, but it doesn't have anything to do with a CD being loaded. It's the Acronis recovery manager giving an opportunity to boot from the recovery CD.

I keep the boot order of our machines: CD, Floppy, HDD.

---

### Post by ssulaco on 2009-12-26
> **michaelvoss said:**
> 
The problem is that when I restart the computer with the live CD in it, 9.04 just boots up every time as normal.
Messing with bios can be bad if you are not careful........once you're in bios navigate to boot sequence,or boot option,dont mess with anything else make sure cdrom is the first boot order,once changed I would leave it at 1st,hardrive at 2nd,because when you empty the cd/dvd rom and reboot,the boot order will skip over the empty rom drive and hit next in line,your hardrive...read this:
[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

---

