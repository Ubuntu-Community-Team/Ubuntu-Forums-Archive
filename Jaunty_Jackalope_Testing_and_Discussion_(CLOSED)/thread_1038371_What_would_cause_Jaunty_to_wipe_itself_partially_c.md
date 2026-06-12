---
title: "What would cause Jaunty to wipe itself partially clean?"
date: 2009-01-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2009-01-12
This afternoon, whilst using Firefox on Jaunty, reading up on the problems with the daily live CD, I found that all of a sudden when I minimised Firefox that the wallpaper had gone, all icons disappeared and most of the filesystem missing.

I've had no logs left, most of the folders missing, my home folder wiped aside from the trash can and the wine directory. Very strange, as I wasn't doing anything before or during the time other than reading forum posts and bug reports on Launchpad. I have since reinstalled Jaunty from the daily ISO (I had to dig out a old PS/2 keyboard to do it as my normal wireless done don't work).

Now I am aware of the dangers of using bleeding edge development versions of software, but I am completely stumped as to what caused a load of files to be wiped? Is it still worth filing a bug report even with no evidence other than my own interpretation of what happened?

---

### Post by scaine on 2009-01-12
Were the files that were wiped root filesystem files?  If so, then something has gone horribly wrong with your install.  Perhaps you were running a root nautilus or something else with root privileges?

Could even be a dead/dying hard disk...?

---

### Post by Gina on 2009-01-12
I suggest running [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and see what remains.  Also, I would run the disk check app.

---

### Post by tghe-retford on 2009-01-12
> **scaine said:**
> Were the files that were wiped root filesystem files?  If so, then something has gone horribly wrong with your install.  Perhaps you were running a root nautilus or something else with root privileges?

Could even be a dead/dying hard disk...?
Dying hard disk was the first thing I feared, so I turned on the SMART checking in the BIOS and no warning of a dying hard disk has appeared. As far as anything to do with root goes, the last thing I did which would have involved root was an update a hour or two previously.

---

### Post by jfernyhough on 2009-01-12
Hard drive failure or drive power loss.

My new laptop drive (grr) had the same problem when the disk stopped spinning.
A backup USB drive install lost power and same thing.

In the case of the internal drive SMART reported nothing wrong at all. On the plus side, the odd trick of heating the drive (on top of a stove, an oven would likely work as well) and putting it back in the laptop worked long enough for me to get the most important data off. Then after 12 hours or so the drive died completely. Now it just beeps softly when powered on and makes regular buzzing noises.

---

### Post by Gina on 2009-01-12
Goes to show the importance of backups - you never know when a hard drive will fail.  Very important data should be backed up several times and kept in several different places.

I'd suggest checking the drive connections.  Bad contacts are often a problem.

---

### Post by plun on 2009-01-12
Its unstable transient conditions for the moment.:)

I totally broke my PC....  no data loss but severe
trouble with kerneloops/freezes. 


"Be careful out there..."

---

