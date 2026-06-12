---
title: "Unable to shutdown my ubuntu 12.10"
date: 2013-05-24
forum: Installation &amp; Upgrades
---

### Post by hanishjadala on 2013-05-24
Hi all, I was unable to restart of shutdown my ubuntu 12.04 laptop so upgraded to 12.10 but still I have same problem. How to solve this issue. I am getting normal shutdown screen with 5 dots moving but it never shutdown. Kindly help me to solve this issue. I have to go with power button to shut down my laptop. it is not proper to go with it.

---

### Post by ohnonot on 2013-05-24
no, that's not good.
is everything else working? did you notice anything?
you could try this:
shut down, and while waiting, press ctrl-alt-F2 (or F3, F4...). this should get you to a login terminal. try logging in from there, and then try to see what's happening, maybe with 'sudo top' or 'sudo htop'. or 'sudo lsof'.
all these commands create lots of cryptic output, but you have to find out what is stalling the shutdown process.

also, this could be hardware related (your laptop).
have you checked your bios? have you made extensive web searches? (also called "g00gle")

also, are you using straight vanilla ubuntu? i think i had similar problems with an lxde-based install (not lubuntu) once and it had sth to do with root privileges. just guessing.

---

