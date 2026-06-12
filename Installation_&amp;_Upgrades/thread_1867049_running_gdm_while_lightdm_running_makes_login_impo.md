---
title: "running gdm while lightdm running makes login impossible"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by fritoz on 2011-10-22
Hello,
I have recently upgraded tp Ubuntu 11.10. Except touchscreen, everything worked seemingly ok.
In the forums I found a temporary repair for the touchscreen. I was trying to have  the repair
run each time I login. Doing that, I started gdm from console, without knowing that 11.10 uses lightdm.

Now I get the lightdm login screen but cannot login. I see a falsh of black screen with a number
of lines, the last of which reads "Stopping System V runlevel compatibility"

I started my computer in "rescue level". In terminal I tried to start gdm or lightgdm, resulting a black screen
and sometimes getting the message above. I suspect the problem is some permission issue.

If anyone can help me, I would appreciate. Otherwise I plan to reinstall 11.10 or downgrade to 11.04.

---

### Post by shadytv on 2011-10-22
im not sure if this will help
try logging in via command line ctrl-alt-F2 (when the error pops up)if that works run sudo dpkg --configure lightdm (or sudo dpkg --configure gdm)
then follow the on screen instructions and choose either gdm or lightdm
hopefully then you'll be able to log in :)

---

### Post by fritoz on 2011-10-22
Thank you shadytv for your quick reply.
I got Ubuntu 11.10 work again. Here is what I did:
* I removed and reinstalled gdm and lightdm.
* Invoking sudo dpkg-configure gdm, I changed to gdm.

Now gdm works. But lightdm does not still work.

---

