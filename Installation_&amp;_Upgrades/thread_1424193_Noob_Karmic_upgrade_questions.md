---
title: "Noob Karmic upgrade questions"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by awang on 2010-03-07
I have a dual boot Vista and Ubuntu, with / and /home on separate partitions.

I upgraded from Jaunty to Karmic last week.  It's mostly working, except no audio and no touchpad.
I'm considering reinstalling fresh to see if that clears up my problems.  I started looking around for instructions to do this, and ran across a couple of concerns:
[LIST]
[*]How do I preserve previously installed applications and settings?  I thought that when I set up / and /home on separate partitions that the OS proper was installed on /, that apps and other user files were installed on /home, and that OS upgrades affected /, but /home was not affected?  Now I'm not sure that is the case.
[*]I read that GRUB 2 can break dual boot?
[*]What kernel should I be running?
[/LIST]

---

### Post by Revolutionary101 on 2010-03-07
To answer your first question about how to save your programs. Install APTonCD to do this.

It will take all of your downloaded programs and write them to a CD. When you reinstall Ubuntu you can just reinstall the programs from the CD. (Although it will not reinstall your previous settings and it only puts your programs in the APT cache so you have to install them yourself.)

As for the other questions you have but I hope my suggestion helps.

---

### Post by awang on 2010-03-11
Audio and touchpad came back after upgrading kernel.

---

