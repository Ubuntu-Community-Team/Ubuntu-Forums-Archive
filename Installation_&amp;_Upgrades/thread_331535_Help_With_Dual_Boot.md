---
title: "Help With Dual Boot"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by 737Best on 2007-01-04
Hi Guys,

This is my first post lol and i am pretty new with linux.  Last night I installed Ubuntu 6.10 on my computer's IDE slave.  My computer runs with windows on an SATA II master hd.  Now the installation of linux was fine, and it said it installed grub on hd0 (which is my SATA master HD) so i figured it would work.  But when I rebooted my computer nothing happened and it just boots into Windows (no grub or anything) And obviously the hd isn't recognized as a boot choice.
I'm not really flexible with my Windows partition because it has a ton of flight simulation stuff on it and I don't want the headache of downloading it again and such.
So pretty much I am wondering how can I enable grub or can I just make the IDE another master and then boot linux that way (my BIOS config lists my first SATA as the secondary master or something like that, and it goes up to the sixth master so i figure there can be more than one?)

Anyways, thanks :)

---

### Post by logos34 on 2007-01-05
the obvious thing to do would be to set the disk boot order in the bios so that your ide slave is first and sata second (or unplug the sata).  If it boots into linux then there's your answer.

Make sure to change the jumper if you make your ide master (unless you use cable select).

---

