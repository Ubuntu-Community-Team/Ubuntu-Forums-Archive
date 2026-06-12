---
title: "ubuntu stalls at battery status"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by danman1453 on 2013-01-28
I upgraded to 12.04 from 11.10.
11.10 ran fine with no modifications.
Now, I cant boot to a gui. The screen shows something about "checking battery status" or something like it. I know thats not the actual problem.
I dont know what logs to inspect to find the problem.

I CAN ctrl-alt-f1 and login. from there i can run startx and get the desktop fine. But, there are a lot of things not loading when i do it that way.

What logs should I be checking to find the problem?

Well, I have my file sharing working again, but still no desktop.

---

### Post by danman1453 on 2013-01-28
nevermind... i got it.

--purge lightdm
install lightgm
install gtk-greeter

logs in, works, end.

---

