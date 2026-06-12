---
title: "Cannot find CD-ROM drive?"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by Cyberflyz on 2007-11-28
Hello,
  I am new to ubuntu. I have been trying to install a 7.10 server edition.
 I get to point where it looks for the CD-ROM drive. The title on the screen is, "Detect and mount CD-ROM"
    It cannot find my CD-ROM drive, so it asks me to manually select a CD-ROM module and device.
What do I do to complete this? I click yes, then it brings up a screen for me to point it in the right direction. I do not know what to do, please help.
               Cyberflyz

---

### Post by Pumalite on 2007-11-28
Post your specs and look in your BIOS; see what options you have.

---

### Post by Cyberflyz on 2007-11-28
INtel Pentium 3
866 MHz
Level 2 cache 256 KB
256 MB SDRAM
10 GB hard drive

---

### Post by Pumalite on 2007-11-28
You should install this if you can set your CD to boot:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Cyberflyz on 2007-11-28
After I get the cd to Boot, the OS cannot find the CD-ROM drive, I can enter where the drive is at manually. I just need to know where the drive is.

---

### Post by Pumalite on 2007-11-28
Have you gone into your BIOS? What did you find?

---

### Post by Cyberflyz on 2007-11-28
In my bios here is my setting:

    I have no Diskettes nor a zip floppy support

Primary drive 0 is my Hard drive
             drive 1 is blank
Secondary drive 0 is my CD-ROM Reader
                  drive 1 is blank
Boot sequence is CD-ROM only

---

### Post by Pumalite on 2007-11-28
Make sure your CD is first in boot order.

---

### Post by Cyberflyz on 2007-11-28
In my install process I get stuck at the Detect and mount CD-ROM.
  This is where I encounter the problem

---

### Post by Pumalite on 2007-11-28
See if you can update your BIOS.

---

### Post by PmDematagoda on 2007-11-28
Could you post the specifications of your PC. From what I can get, you seem to be having an old BIOS.

---

### Post by Cyberflyz on 2007-11-29
Ok, I updated my bios...however it stills says DURING the installtion of Ubuntu...that I am missing the module....so what should i try next.

*edit
    Well the computer I am using is an old Optiplex GX110....its bios is now version A09...the rest of the specs are on a the first page, of this thread.

---

### Post by PmDematagoda on 2007-11-29
Did you burn the Live CD properly? If you burnt the Live CD at a speed greater than 4X then the Live CD may be corrupted.

---

### Post by Cyberflyz on 2007-11-29
Ok, i created another cd at a lower speed. And It still asks for me to locate the CD-ROM module....I don't know what to do

---

### Post by Cyberflyz on 2007-11-29
Ok, I fix the problem...Ubuntu didnt have a driver for my cd-rom reader! But I changed it out with a better one...so now I have it running...
    Thanks!

---

### Post by Pumalite on 2007-11-29
Good luck.

---

