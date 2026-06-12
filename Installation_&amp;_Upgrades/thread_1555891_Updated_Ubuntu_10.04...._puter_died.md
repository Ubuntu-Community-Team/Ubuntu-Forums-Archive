---
title: "Updated Ubuntu 10.04.... puter died"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by ljmccrea on 2010-08-18
I recently wiped my son's computer of windows and installed ubuntu 10.04 from the live cd.  It runs great until we do the updates thru the update manager.  upon reboot (as requested from updater)  we get all sorts of code. then nothing.  At one point as I"m trying to read what is going up the screen, I have seen something along lines of unexpected disengaged.  Not sure what was disengaged, and I"ve tried to read forums to fix it, with the live cd.... I guess I"m not smart enough to fix this... any pointers?  Ubuntu is the only thing on my son's computer.  I have at one point, gotten a login prompt. in just a black screen with letters everywhere.   I can log in but I"m not yet famiier with the language.  I'm guessing it's a video driver issue, not sure.  I've tried to edit my /ect/default/grub but everytime I try using vi or nano it opens a new doc, and I"m not able to access the actual one.

---

### Post by arpanaut on 2010-08-18
Have you tried booting from "recovery mode" at the grub menu.
You will have to tap "shift" continuosly after bios post to get to that menu 
as by default with single OS install the menu will not show.

After entering recovery select "fix broken packages" then try to boot into safe graphic mode (or something similar) 

hope that helps get you started back.

---

### Post by jimbop99 on 2010-08-18
I recently screwed up grub and this helped. Near the bottom is how to reinstall grub from a live cd.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by mörgæs on 2010-08-18
Yes, that is a good beginning. 

After that: If the system is stable enough, please post the output from the command 

```
 hwinfo --gfx
```

---

### Post by ljmccrea on 2010-08-18
ok did the shift key trick and still nothing....  going to try to reinstall grub tomorrow, just got home from school and son's computer is in his room.  (no access)  will update after attempt.  Thanks for the help.

---

### Post by ljmccrea on 2010-08-21
Thanks for the help.... I did finally manage to get a command line and did another update via command line.  It was still messed up a little bit. So I reset bios to default... running like a champ.  now to get world of warcraft up and running....  Thanks again ya'll.

---

