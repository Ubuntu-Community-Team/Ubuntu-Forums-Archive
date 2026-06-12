---
title: "Install XP on same disk as Ubuntu and Vista"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by sept298901 on 2008-07-09
Hey, i have a little problem, i am mainly a windows person, but over the last few months i have been using Linux more and more because it doesn't crash like my vista OS does.  as you all know the downside to Linux is gaming, and since i am running vista x64 i can't install half of my old games that i really like.

What i want to do is install xp on my machine.  At the moment i have GRUB set up to boot Vista first and Ubuntu if i select it.

any help would be appreciated, thanks.

by the way i have to latest x64 version of ubuntu installed if that helps.

---

### Post by xp_newbie on 2008-07-09
There shouldn't be a problem if you follow the following general steps:
[LIST=1]
[*]Create an empty (unformatted) partition
[*]Install XP on it. Do not let it install in either the Vista or Ubuntu partition.
[*]Configure GRUB to add XP as another boot (/boot/grub/menu.lst)
[/LIST]

HTH,
Alex

---

### Post by sept298901 on 2008-07-10
i guess my question is then, how do i configure grub, and when i install xp will it automatically boot to that right off the bat?

---

### Post by jimv on 2008-07-10
Install it OVER Vista....two problems solved at once.

---

### Post by sept298901 on 2008-07-10
i need a 64 bit windows operating system, and xp x64 stinks.  so unfortunately vista is my only option if i want to use windows programs with over 4gb of ram.  i hear where you are coming from though, i really hate vista with a passion.

---

### Post by jimv on 2008-07-10
> **sept298901 said:**
> i need a 64 bit windows operating system, and xp x64 stinks.  so unfortunately vista is my only option if i want to use windows programs with over 4gb of ram.  i hear where you are coming from though, i really hate vista with a passion.

Heh, I just "upgraded" to XP again last week.  I had Vista for almost a year and I just couldn't take it anymore.  I forgot how fast my computer was :)

---

