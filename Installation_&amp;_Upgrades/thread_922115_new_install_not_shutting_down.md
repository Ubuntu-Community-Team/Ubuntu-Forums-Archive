---
title: "new install not shutting down"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by bujums on 2008-09-17
I have an older computer with newly installed Kubuntu 8.04 all is well except that when I run shutdown it does everything but then sais  something like "system halted" but does not really turn off.  I had Ubuntu 7.10 on the same computer and it did the same thing. Could someone tell me the fix please.  I would not really worry about this but I am giving the computer to a family and I want it to function properly.

p.s. I have done a little stuff in the terminal but not much.

---

### Post by confused57 on 2008-09-17
You could try:
```
kdesu kwrite /etc/modules
```

add the following line:
```
apm power_off=1
```

---

### Post by Sef on 2008-09-17
> confused57 	 		**Re: new install not shutting down**
 		You could try:
 	Code:
 	kdesu kwrite /etc/modules 
add the following line:
 	Code:
 	apm power_off=1 


You can copy and paste those commands instead of typing them, if you so choose.

---

