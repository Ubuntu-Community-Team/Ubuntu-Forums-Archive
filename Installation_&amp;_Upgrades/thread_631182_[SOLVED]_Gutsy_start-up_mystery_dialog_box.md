---
title: "[SOLVED] Gutsy start-up mystery dialog box"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by GaryUK on 2007-12-04
Dear All,

So I upgraded from Feisty to Gutsy with some considerable trouble as the upgrade process hung in the middle and I ended up with half a system. I have managed to resolve all of my issues except for one - see file attached.

I have a mystery dialog box that comes up after initial boot into Gnome saying simply that a file has not been found and so therefore it has failed to load. The thing is - I cannot find this error logged anywhere.

I have checked the system logs; the X.org logs; tried shutting down services and restarting;reinstalled the PAM keyring files; reinstalled gnome and reinstalled the Ubuntu desktop. I have even managed to reinstall compiz fusion and got that working with emerald. What I have not been able to do is find this darned file that is missing.

Does anyone know where the appearance of such a dialog box would be logged or know of a way to force logging so that I can find what is missing?

All suggestions gratefully received.......

Regards and Thanks in Advance!

---

### Post by Pumalite on 2007-12-04
Post:
dmesg

---

### Post by GaryUK on 2007-12-04
Pumalite,

As requested, dmesg output attached - I issued the command "dmesg >> *filename*" which I hope is correct. I am aware of USB errors on my powered USB hub but I do not think that is the issue - it never caused a problem under Feisty and I used to get the same messages there.

I still think it is a missing file rather than any read/write errors.

Thanks for you help !

---

### Post by GaryUK on 2008-02-02
I am marking this thread as solved as I have found the offending file/software. It turned out to be OnTV, so I uninstalled it and removed from the panel and the file not found dialog went away.

I then re-installed, and followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=370534&highlight=ontv]("http://ubuntuforums.org/showthread.php?t=370534&highlight=ontv")

and that fixed the problem.

---

