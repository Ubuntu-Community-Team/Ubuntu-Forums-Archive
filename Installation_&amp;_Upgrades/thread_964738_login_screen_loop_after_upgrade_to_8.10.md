---
title: "login screen loop after upgrade to 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by siklosi on 2008-10-31
Hi,
I just upgraded from 8.04 to 8.10. After restart I'm getting log in screen that constantly restarts. I see ubuntu logo with username box for split of a second and then it disappears for second or two with only grey screen and appears again for split of second...

---

### Post by SigmundFreud on 2008-10-31
I had something like this (with Kubuntu). After a lot of searching I disabled DRI in xorg.conf (option "NoDRI" or something) and after that KDE 4 at least started.

---

### Post by Kirked on 2008-10-31
Same problem at Server Edition. Cannot login after upgrading. SSH also disconnected after entering login and password.

---

### Post by modemlamer on 2008-11-20
same problem!

but after normal restart!

gmd login stays in loop

console login stays in loop

and even login via ssh isn't possible!

only login by root-console in recovery-mode works

but wenn ich switch in runlevel 2,3 etc. i still cant login!


any ideas? except reinstalling the machine?

---

### Post by zenkoanlife on 2008-11-26
take a look at this post
h[ttp://ubuntuforums.org/showthread.php?t=975890]("http://ubuntuforums.org/showthread.php?t=975890")

---

