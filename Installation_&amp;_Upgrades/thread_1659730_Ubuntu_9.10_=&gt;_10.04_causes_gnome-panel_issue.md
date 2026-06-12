---
title: "Ubuntu 9.10 =&gt; 10.04 causes gnome-panel issue"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by s3a on 2011-01-04
The upgrade messed up my gnome-panel. When on the tty1 console, I enter *sudo killall gnome-panel && sudo gnome-panel* and then it works but how do I fix this the "normal way" so that it can be normal as of the startup without any manual interference?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by dino99 on 2011-01-04
into your /home the hidden .gconf folder might be corrupted: remove it (or rename it) it be be recreated on next boot

---

### Post by s3a on 2011-01-05
Actually, I tried and it didn't solve anything so I put back the .gconf folder I had. In fact, I forgot to mention that my account works perfectly and that's it's just my mother's account that has a messed up .gconf folder. When I renamed the folder, I didn't check my account but hers was messed up from scratch. I had to reput the buttons on the right side (as is expected) but all the other issues reappeared.

---

### Post by s3a on 2011-01-05
Bump (I really would like to fix this issue)

---

### Post by s3a on 2011-01-09
Removing compiz and compiz-core fixed it but then I re-installed them and removed them again and now I have a problem where the workspaces go from 4 to 1 and the window border dissapears. When I run the metacity command, all is well but I have to do it upon each login and my mom is not too computer saavy and I don't want to tell my computer to run the metacity command upon each one of her logins since that's not the proper way to fix it. Removing the .gconf folder actually has an effect now. It feels like Ubuntu 10.04 from scratch when I do that but I had her account configured so "feminine" and I really don't feel like doing it all over again.

**Basically**, removing .gconf is a proper but long solution. So, a good question (in my opinion) is: _Which sub-folder/sub-directory must I remove in order to solve the issue without having to reconfigure everything else?_ (I tried removing the compiz folder and that didn't do anything).

---

### Post by s3a on 2011-01-10
I just wanted to add that my account works perfectly during all this.

---

