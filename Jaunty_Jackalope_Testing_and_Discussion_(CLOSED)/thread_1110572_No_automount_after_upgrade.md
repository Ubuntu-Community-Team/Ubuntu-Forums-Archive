---
title: "No automount after upgrade?"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mud.Knee.Havoc on 2009-03-29
I upgraded to Jaunty the other day, but just noticed that it won't automount my MP3 player (Sansa E270) like it used to.  It shows up with dmesg, however, which is a good sign.

Does anybody have any ideas?

EDIT: I should mention that most of the problems I've seen while googling show that people must go to the System->Preferences->Removable Drives and Media utility, then select either Storage (as it's seen as USB storage) or Multimedia (to auto-play in an audio program, I assume).  I have neither tab in my Removable Drives and Media utility.

---

### Post by adoyle626 on 2009-03-30
When you installed 9.04, did it make you remove any programs?
I know when I downloaded 9.04 from 8.10 that I had 35 programs it wanted me to get rid of.

---

### Post by lithorus on 2009-03-30
The "System->Preferences->Removable Drives and Media utility" is in the gnome-volume-manager package. Try and install that..

---

### Post by Mud.Knee.Havoc on 2009-03-30
@adoyle626: It did make me remove some programs when I upgraded.  I had taken a look at the list and reinstalled some of the stuff when I got back up and running, but maybe I am missing something important.  Good advice to anybody upgrading: make note of the programs that will be removed! :)

@lithorus: That program was uninstalled upon upgrade, but even after installation, I still cannot mount my Sansa.  I still don't have any "storage" or "multimedia" tabs in the Removable Drives utility.  Strangely enough, it *does* automount normal USB sticks.  I have tested the Sansa on my Ubuntu 8.10 laptop and it works perfectly.

Oh well, if I can't get this working (or even if I can), I'll probably be doing a fresh reinstall when the RC comes out. :)

---

