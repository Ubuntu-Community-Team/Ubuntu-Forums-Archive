---
title: "System boots slow after upgrade 10.04"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by DawgMan on 2010-11-29
After my upgrade the bootup seems to take a long time.  I am dual booting with XP.  From the boot menu when I select Ubuntu it takes 35 seconds before I get the login screen.

Is this normal?

Also, other apps seem to be running slow.  Running Win 7 under VMWare Workstation 7.1.

---

### Post by Rubi1200 on 2010-11-29
35 seconds is about what it takes on my laptop which is 7 years old. Once booted to the desktop, though, it is super fast and responsive so I don't mind the slightly longer boot times than those I have seen other users reporting (ranges from 10-20 seconds in many cases).

However, you may want to look at things like the amount of RAM you have installed, reducing the number of applications that are set to run at startup etc. Graphics could also be an issue; check whether you have desktop effects enabled and turn it off.

---

### Post by siddarthkaki on 2010-11-29
Well, boot speed depends on how old your system is. Have you tried Computer Janitor (System>>Administration>>Computer Janitor)?

---

### Post by DawgMan on 2010-11-29
I've never used the computer janitor. I lists packages that I use. What is it really going to remove?

Some packages listed that are of concern:

TrueCrypt: it says the size is 0 B. so what is it going to remove? I use truecrypt all the time.

vmware-workstation: is says the size is 396 MB.  I use this everyday.  I the computer janitor going to remove it?

---

### Post by siddarthkaki on 2010-11-29
Sorry, but I am not completely familiar with the Computer Janitor myself. Perhaps the packages that it displays are older version? That has happened to me before. How old is your system?

---

### Post by DawgMan on 2010-11-29
my system is only 3 years old.  VMWare has been updated several times and TrueCrypt has never been updated that I know of.

Thanks for the help.  I will find more intel on the Computer Janitor.  Worst case I will uncheck the questionable items.

---

### Post by Rubi1200 on 2010-11-30
My advice is to not use Computer Janitor at all!!

I have seen too many posts from users who "accidentally" deleted stuff that it recommended could be cleaned up.

If you want to do some "housecleaning," refer to this:
[http://ubuntuforums.org/showthread.php?t=140920&highlight=remove+unneeded+junk](http://ubuntuforums.org/showthread.php?t=140920&highlight=remove+unneeded+junk)

---

### Post by siddarthkaki on 2010-12-01
I am not sure, but this might help: Try cleaning out the auto-removable and obsolete packages in Synaptic. Those subcategories should be in Status in the lower left hand corner.This can also be done in the terminal.

---

