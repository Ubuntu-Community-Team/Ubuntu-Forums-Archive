---
title: "Video problems during install?"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by Meilichios on 2006-12-18
Ok... I'm running an 64bit AMD on an Nforce 4 board w/ a gf6600. I have two SATA 300GB HDs on RAID w/ WinXP Pro. installed on it, and an IDE 120GB that I want to install Xubuntu 6.10 on and then dual boot them.

When I boot off the CD, the menu comes up, and I choose install Xubuntu, it shows the loading menu, once it's done loading, the screen turns into a bunch of different colored vertical all over the monitor. And I can't do anything from there, and have to reset the system.

I boot off the CD again, and do the safe graphics mode, but there's no cursor, and I can't figure out how to get it to work? Are there drivers I need to install to get this to work or what should I do?

Any input would be appreciated.

---

### Post by wpshooter on 2006-12-18
Might want to try the ALTERNATE CD installation.

---

### Post by Meilichios on 2006-12-19
Ok, got it installed, it went just fine.
Got to where it said it was gonna eject the CD and I need to restart and then do the user settings, I hit continue, it boots up, looks good.. then it gives me all the vertical lines again. It makes some sound from the speakers and that's it.

---

### Post by Meilichios on 2006-12-19
Err, I mean.. 
I downloaded the alternate CD, got it installed, and it still does the same thing once it gets to where I believe it should be showing the desktop.

---

### Post by dinub1 on 2006-12-20
Are you using an ATI Radeon PCI-E type of graphic card?

---

### Post by Meilichios on 2006-12-20
No, I'm using a GeForce 6600.

---

### Post by Titus A Duxass on 2006-12-20
Try adding vga=771 as a boot option, if you have an installed system you can do this by pressing Esc when prompted by GRUB.  Then tab to the correct line, should be the first, press "e" to edit, then tab to the line with the with the details (will contain someting like 2.6.17.... etc.) and add vga=771 to the end of the line, then boot by pressing "b".

I am going from memory here, do a search for vga=771 for more details.

---

### Post by Meilichios on 2006-12-20
Ok, I added the VGA=771 to the end of the kernel line in the boot program. When it loaded Ubuntu, the video was still all scrambled, but it was offset to the side, so I'm guessing it was running at a lower resolution that I haven't set the monitor up for yet. So I know it did something.. but still didn't fix the problem.

Is there any other information about my computer that I should give that would help figure out what the problem is?

---

### Post by Meilichios on 2006-12-22
No ideas, anyone?

---

