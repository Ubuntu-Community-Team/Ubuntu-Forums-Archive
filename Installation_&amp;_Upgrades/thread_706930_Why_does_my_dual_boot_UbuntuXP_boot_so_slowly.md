---
title: "Why does my dual boot Ubuntu/XP boot so slowly?"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by JEBB on 2008-02-24
I added Ubuntu 7.10 to my XP machine's hard drive (a Thinkpad R40) and, after solving a few problems with help from this forum, both operating systems run fine once they get started.  

Getting started is the problem.  Ubuntu takes a very long time, several minutes,  to load whereas XP starts right away.  It is much slower on this Thinkpad than on an old 400MHz K6 Compaq.  Is there a way to speed up the loading of Ubuntu?  Ubuntu is listed first on the list of choices when I start the computer.

---

### Post by pytheas22 on 2008-02-24
take a look at [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) .  There are things you can do to make it boot faster.

---

### Post by JEBB on 2008-02-25
That reference gives more than I want to learn or try.  If that's the only way to speed up Ubuntu booting in a dual boot system, I'll live with what I have.   

I've got a lot of other projects to complete and don't have the time to learn all that.  If anyone can give me a simpler way to achieve what I need, I'd appreciate it very much.

---

### Post by pytheas22 on 2008-02-25
That reference turns out to be outdated anyway; sorry.  I don't know of any one-minute solutions to getting a faster boot time.  But if your boot is taking extraordinarily long, maybe there's something strange going on.  Press control-alt-f1 as soon as the Ubuntu splash screen comes up and you will see what it's doing step-by-step as it boots--if it's hanging on a certain step, you may be able to figure out what's wrong.

Ubuntu does take longer to boot than Windows (at least, to get to the login screen--Windows in my experience can still take minutes to finish loading the desktop and background services after you log in, whereas Ubuntu is actually mostly started and only needs to load Gnome), but it shouldn't be taking you longer than two minutes maximum on a modern machine.  My Pentium IV 2500mhz/512 MB machine boots in under that easily, and that computer is sort of old.

---

### Post by Pumalite on 2008-02-25
Edit /boot/grub/menu.lst and remove 'quiet splash' from the kernel line.

---

