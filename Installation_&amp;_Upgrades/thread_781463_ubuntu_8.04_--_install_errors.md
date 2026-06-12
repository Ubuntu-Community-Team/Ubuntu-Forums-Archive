---
title: "ubuntu 8.04 -- install errors"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by jojokdh on 2008-05-04
Hi --
   I downloaded the desktop version, checked the md5 sum, copied it to CD, changed the boot sequence (I'm trying to overwrite Vista, which drives me crazy).  Tons of errors coming up --
SQUASHFS error: unable to read page, unable to read fragment cache block whatever, sb_bread failed reading block whatever, and also Buffer I/O error on device sr0 errors.
   I know this desktop has 2 discs, and one is used by Vista for backup;  is this causing problems?

What do I do now?  

signed, lost after Windows.  ;-p

thanks!!

---

### Post by Pumalite on 2008-05-04
Can you boot a Live CD?

---

### Post by jojokdh on 2008-05-04
Sorry for my ignorance.  Is the distribution I downloaded from ubuntu.com NOT a "live" cd?  If not, where should I obtain one?

---

### Post by Pumalite on 2008-05-04
Boot from your Ubuntu CD and post from the Terminal:
sudo fdisk -l

---

### Post by jojokdh on 2008-05-04
Um, at what point in the booting process do I stop it (how), and then type in that command?  
   It's still doing those errors from the earlier attempt, and Cntl-alt-del is not stopping it.  No response to esc or any f keys either.  Do I eject the disk or unplug to stop it??

--jo

---

### Post by Pumalite on 2008-05-04
Let it boot. You have to get all the way to the Desktop. There go to Applications>Accessories>Terminal. Copy and paste the command there. Hit 'Enter'. Copy and paste the output here.

---

### Post by jojokdh on 2008-05-04
okay... if it ever quits.  It's been an hour now, and it's still spitting errors onto the screen.

thanks!

---

### Post by Pumalite on 2008-05-04
Looks like you are going to have to install with the Alternate CD. Or burn a new CD after doing md54sum and burning at 4x or less.

---

### Post by jojokdh on 2008-05-04
so, you think it's a bad copy then, despite the md5 checksum I ran?
Okay, I'll try downloading a second time.
thanks!

---

### Post by Pumalite on 2008-05-04
If md5sum was correct, then the suspect is your burner. Burn at 1x after cleaning the lens. Check CD integrity before install. Try your CD in a different computer.

---

