---
title: "Mother in Law's (MIL) old monitor in triplicate!"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Jose Catre-Vandis on 2006-06-04
I ran an installation of dapper 6.06 for my MIL, having brought her shuttle box home. I used an AOC 17" to see what was going on. She has a Shuttle SN43G which has onboard Nvidia graphics card. I didn't install any specific graphics drivers, I just let dapper do its stuff.

The box has gone back to the MIL. She connected up and booted fine, but she is getting dapper in triplicate (three views overlapping across the screen) on her old Packard Bell 15" monitor.

Anyone know what is going on here, and how I can fix it. I think it is something to do with resolution, so is it simply a matter of editing xorg.conf at the command line?

---

### Post by John.Michael.Kane on 2006-06-04
**Deleted......**

---

### Post by az on 2006-06-04
This is a bug that probably will be addressed in the near furture.  It used to be that you booted a Unix box and all the hardware stayed the same.  This is not so for desktop computers and there still is a little ways to go to get there.

X hardware is detected only once - at install time.  You need to redo autodetection.

Boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg

and then run

init 2

and all will be well....

---

### Post by Jose Catre-Vandis on 2006-06-04
[QUOTE=azz]This is a bug that probably will be addressed in the near furture.  It used to be that you booted a Unix box and all the hardware stayed the same.  This is not so for desktop computers and there still is a little ways to go to get there.

X hardware is detected only once - at install time.  You need to redo autodetection.

Boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg

and then run

init 2

and all will be well....[/QUOTE]


Thanks Azz, exactly what I needed to know :D

---

### Post by flip314 on 2006-06-05
In case you were wondering, it sounds like either the desktop was set up for too high a resolution, or at a good resolution with the wrong refresh rate.  More likely the latter, but the former is still possible.

---

### Post by Jose Catre-Vandis on 2006-06-05
[QUOTE=flip314]In case you were wondering, it sounds like either the desktop was set up for too high a resolution, or at a good resolution with the wrong refresh rate.  More likely the latter, but the former is still possible.[/QUOTE]

Yep, I had a similar problem when I set up the box for XP a couple of years ago, but there was no command line to drop to to fix it :wink: 

When installing ubuntu I had forgotten about the ancient monitor again!

---

### Post by flip314 on 2006-06-06
[QUOTE=Jose Catre-Vandis]Yep, I had a similar problem when I set up the box for XP a couple of years ago, but there was no command line to drop to to fix it :wink: 

When installing ubuntu I had forgotten about the ancient monitor again![/QUOTE]

Under windows I learned how to change resolutions without looking at the monitor :cool:   Restarting in safe mode was such a pain.

---

### Post by Jose Catre-Vandis on 2006-06-07
Well after six tries at typing out the command, the MIL got it, and now has her ubuntu 6.0.6 desktop :-) Looks like it can only run at 640x480 though.

---

