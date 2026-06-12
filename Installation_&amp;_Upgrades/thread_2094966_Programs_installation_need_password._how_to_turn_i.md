---
title: "Programs installation need password. how to turn it of ?"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by sebastarzak on 2012-12-15
Hello all !
I need help. Do you know How to turn off password user authentication during installation/update programs ? It's possible?
Thanks 4 all replies ;-)

---

### Post by Cheesemill on 2012-12-15
It is possible but it's not a good idea as it makes your machine less secure.

Why do you want to do this?

---

### Post by sebastarzak on 2012-12-15
Because my computer is only...my. Nobody don't use this machine. Only me. And when I want Install any program i must write my password again again again.. It is boring ;D and i like combine with OS. Probably when i set "Automatic login" to ON, I get what i want. I'm right?
could you tell my what i must do to get settings which i want?

---

### Post by dino99 on 2012-12-15
[http://www.google.fr/#hl=fr&safe=off&tbo=d&sclient=psy-ab&q=ubuntu+password+removal&oq=ubuntu+password+removal&gs_l=hp.3..0i19j0i30i19j0i8i10i30i19l2.18127.22467.1.22856.10.10.0.0.0.0.151.572.9j1.10.0...0.0...1c.1.xxA8vVV_w80&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&bvm=bv.1355325884,d.d2k&fp=ac9d2c5f7cf2a4ff&bpcl=39967673&biw=1485&bih=909](http://www.google.fr/#hl=fr&safe=off&tbo=d&sclient=psy-ab&q=ubuntu+password+removal&oq=ubuntu+password+removal&gs_l=hp.3..0i19j0i30i19j0i8i10i30i19l2.18127.22467.1.22856.10.10.0.0.0.0.151.572.9j1.10.0...0.0...1c.1.xxA8vVV_w80&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&bvm=bv.1355325884,d.d2k&fp=ac9d2c5f7cf2a4ff&bpcl=39967673&biw=1485&bih=909)

---

### Post by MG&amp;TL on 2012-12-15
> **sebastarzak said:**
> Because my computer is only...my. Nobody don't use this machine. Only me. And when I want Install any program i must write my password again again again.. It is boring ;D and i like combine with OS. Probably when i set "Automatic login" to ON, I get what i want. I'm right?

I must stress that it's really a bad idea. And no, automatic login won't do it, that will log you in straight away from the login screen.

As it is, the only real way to do this AFAIK is this: [Root Login]("https://help.ubuntu.com/community/RootSudo") ...read the page in its entirity. Read carefully and understand the problems that can result.

---

### Post by sebastarzak on 2012-12-15
Ok thanks for all replies! 
Greetings, Sebastian ;-)

---

### Post by Cheesemill on 2012-12-15
> **MG&TL said:**
> As it is, the only real way to do this AFAIK is this: [Root Login]("https://help.ubuntu.com/community/RootSudo") ...read the page in its entirity. Read carefully and understand the problems that can result.

You don't need to go down this route, there is a more secure way of doing things.

To allow any user to install programs without enabling the root account you can edit the policykit settings, I've outlined the procedure in this thread:
[http://ubuntuforums.org/showthread.php?t=2080667](http://ubuntuforums.org/showthread.php?t=2080667)

However, I would really recommend not doing this.

> Because my computer is only...my. Nobody don't use this machine
Having an insecure system doesn't just affect you, if your system is compromised it can affect everyone that uses the internet (bot-nets, DDOS, open mail relay etc.).

---

### Post by MG&amp;TL on 2012-12-15
> **Cheesemill said:**
> You don't need to go down this route, there is a more secure way of doing things.


Neat, thanks! Although I recommend the OP reads the link anyway, knowing how the system works is never a bad thing.

---

