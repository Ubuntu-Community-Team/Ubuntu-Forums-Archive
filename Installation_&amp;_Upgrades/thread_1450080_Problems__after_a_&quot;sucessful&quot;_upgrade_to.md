---
title: "Problems  after a &quot;sucessful&quot; upgrade to 10.04"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by cest42 on 2010-04-08
I recently upgraded from 9.10 to 10.04 and all went well once I found the trick to force the upgrade to a beta version. (Subject of a previous post)

 However now having switched the PC back on after 2/3 days of not touching it, I have nothing in the top and bottom menu bars, just the icons on the desktop for the CD and a shared drive (Machine is dual boot XP/Ubuntiu courtesy of Wubi). I can change back ground but little else

Can anyone suggest what has gone wrong and point me at a solution ?

Steve

---

### Post by cest42 on 2010-04-09
I have now decided I "just" have a corrupted Gnome installation so will switch to the Desktop forum.

---

### Post by garvinrick4 on 2010-04-09
> **cest42 said:**
> I recently upgraded from 9.10 to 10.04 and all went well once I found the trick to force the upgrade to a beta version. (Subject of a previous post)

 However now having switched the PC back on after 2/3 days of not touching it, I have nothing in the top and bottom menu bars, just the icons on the desktop for the CD and a shared drive (Machine is dual boot XP/Ubuntiu courtesy of Wubi). I can change back ground but little else

Can anyone suggest what has gone wrong and point me at a solution ?

Steveright click on desktop create launcher and then in command make 
gnome-panel in other boxes whatever you want. Click OK

---

### Post by cest42 on 2010-04-09
Thanks for that , will give it a try later.

Through searching I have seen there is a known bug that matches what I have

"depency conflict  with libgjs0 and xulrunner" here> [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/555155](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/555155)

Steve

---

### Post by garvinrick4 on 2010-04-09
> **cest42 said:**
> Thanks for that , will give it a try later.

Through searching I have seen there is a known bug that matches what I have

"depency conflict  with libgjs0 and xulrunner" here> [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/555155](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/555155)

SteveGnome-shell is a whole different animal, you are not using it. Confusing the name of that package it is wanting to replace gnome desktop.. Use this code to check out what a package does Code:

aptitude show (package name)

Like gnome-shell

aptitude show gnome-shell

---

### Post by cest42 on 2010-04-09
Thanks again for the input but it didn't work so I reinstalled 10.04 and was in same situation so deleted the original installation + Wubi and am just defragging the disk before reinstalling. Will try a clean install of 10.04 rather than an upgrade


Thank you again for the suggestions

S

---

