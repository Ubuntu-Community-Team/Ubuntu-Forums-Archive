---
title: "white screen on boot after upgrade to 9.10 from 9.04"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by sosrip14 on 2009-11-27
Hey guys,
A severe problem appears to have occurred with my system. I recently upgraded from 9.04 to 9.10, and after restarting I was greeted first by the old 9.04 boot splash, and then the new 9.10 loading screen, and then finally a white screen with the cursor in the middle. I am unable to move the cursor with my touch pad (I have a Dell Inspiron 1520 with Intel X3100 graphics), however I can move it with my regular external mouse. Has anyone else experienced this problem? Thanks in advance for your help.

---

### Post by lemming465 on 2009-11-28
You aren't the only one who has seen the problem, but I'm not aware of a solution yet, sorry.  If using Ctrl-Alt-F1 to switch to a text console works, try logging in and running a command line update, such as *sudo aptitude update; sudo aptitude full-upgrade* and see if things improve.  If not, you may need to reinstall with 9.04 and wait for better days to upgrade.

---

### Post by sosrip14 on 2009-11-28
> **lemming465 said:**
> You aren't the only one who has seen the problem, but I'm not aware of a solution yet, sorry.  If using Ctrl-Alt-F1 to switch to a text console works, try logging in and running a command line update, such as *sudo aptitude update; sudo aptitude full-upgrade* and see if things improve.  If not, you may need to reinstall with 9.04 and wait for better days to upgrade.

thanks for the reply, I'll try that and if it doesn't work, I guess I'll have to reinstall.

---

