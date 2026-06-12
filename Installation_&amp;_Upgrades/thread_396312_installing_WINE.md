---
title: "installing WINE?"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by xelapond on 2007-03-29
i thought i installed wine correctly(i followed tge AMD64 wiki on the WINEHQ website) but when i type wine, or winefile i get:

alex@alex-desktop:~$ winefile
exec: 29: /usr/bin/wine: not found

Scarrier, when i type man wine, it shows me the manual.

What should i do?  How should i install it properly?

BTW, i am running Edgy Eft on an AMD64 machine

---

### Post by mys_shekar on 2007-03-29
I followed the procedure described in the link below: And it worked well for me. Hope it helps you..

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

shekar

---

### Post by xelapond on 2007-03-29
Thanks, i tried that and i get the following when i try to run wine:

alex@alex-desktop:~$ wine
bash: /usr/bin/wine: No such file or directory
alex@alex-desktop:~$ 

Am i missing something?

---

### Post by RockabillySamurai on 2007-03-31
I used automatix to install wine and that worked pretty well.  Nothing like getting something else to do your work for you!  :P  Maybe give that a try, it could help.

---

### Post by Majorix on 2007-03-31
Tried completely removing and reinstalling? It won't hurt and it could be the fix.

---

### Post by zvacet on 2007-04-01
The step you are missing is 
```
winecfg
```

that command will configure wine

---

