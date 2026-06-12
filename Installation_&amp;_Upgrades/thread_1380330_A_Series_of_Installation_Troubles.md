---
title: "A Series of Installation Troubles"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by RedBirdM on 2010-01-13
Disclaimer:  I have never used Ubuntu or any other form of Linux.  I've never used an operating system that wasn't windows or DOS actually.


I burned the Ubuntu Live CD (Karmic Koala) at work and brought it home for a trial run.  

Booted from the CD with no issues and played around for a couple of minutes, setting up my wireless connection and looking around.  Everything looks just lovely and I'm very excited at the prospect of leaving Windows.  Then it froze.  

Reboot, look around.  Freezes again.

Now I'm thinking: screw it, lets just go for the install.

Reboot.  Click on Install.  Goes through the same steps as if its loading as before.  Nothing.  Just keeps loading.  No prompts for any info, choices or anything.

Reboot.  Trying to just load the OS again without install.  Ten munutes or more to load this time and I get the desktop background loaded fine while the top bar and bottom bar are just flashing on and off non-stop and this error message is displayed in the upper left:

Panel Encountered a problem while loading "OFAID:Gnome_windowlistapplet"

Nothing works.  Can't click to delete or not delete. 

Reboot.  Try to install again.  Lots of error messages, couldn't write them all down.  Here are a couple that were repeated many times:

"cannot execute install: Input/Output Error"
"... debconf-communicate: input/output error"
"Buffer I/O error on device SR0"

I've scoured the forums and nobody seems to have quite the same problems.  Many I/O errors seem to be coming at a later stage and people with installation problems seem to be getting to some sort of install screen that I've never even seen yet.

Please help.  Was very Excited at 6:30 pm yesterday.  Less excited at 1:30 am.  

Thanks,

Jon

---

### Post by RedBirdM on 2010-01-13
I have 5 pages of notes I wrote down regarding my error messages.  None of them, when searched for, produce anything useful or seemingly even related to my installation problems.

Anybody?

---

### Post by presence1960 on 2010-01-13
> **RedBirdM said:**
> I have 5 pages of notes I wrote down regarding my error messages.  None of them, when searched for, produce anything useful or seemingly even related to my installation problems.

Anybody?

sounds like a bad burn or a burn from a corrupted iso.

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso prior to burning as an image to CD? The hashes must match exactly character for character. If even one is off the iso is corrupted.

Did you burn the iso as an image at a slow speed (4x-8x is perfect)? Fast burns are ok for data but for a bootable image often no good. One error and the image is rendered useless.

Boot the CD and choose "check disk for defects" prior to doing anything with the disk.

---

### Post by RedBirdM on 2010-01-13
I did the "check disk for defects" option and it found no defects.

---

### Post by presence1960 on 2010-01-13
OK if the disk is ok then the next thing to scrutinize is your optical drive. If you have another bootabke CD/DVD such as windows try booting that and see what happens.

---

