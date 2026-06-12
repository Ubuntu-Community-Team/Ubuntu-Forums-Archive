---
title: "Programs install on /usr/local - root privileges"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by roscoetuff on 2007-06-30
Okay... my Moneydance program installed on root's /usr/local directory - sub /moneydance. 
Problem is that I can't even run the doggone thing: I don't have privileges and the logon screen won't let me logon as root to change this. What's a frustrated user to do?

Thanks!
JWM

---

### Post by arvevans on 2007-06-30
In the command line interface, use "sudo your_command" to execute a command as root.
"gksudo" works for calling graphical screen commands with root privileges.

Ubuntu does not normally support a root login or su to root from other logins.  Only the first user ID defined at install time will normally have sudo privledges (it uses that user's password), but this can be changed in the user administration screen.
_._

---

### Post by roscoetuff on 2007-06-30
Installation was done per following: sudo ./moneydance ...
So I used my privileges there. I don't understand how this install got screwed up. What to do?

Basically need to change privileges. Had this problem similarly ... though surely different with my iPod and never figured that out. Suggestions?

---

