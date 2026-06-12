---
title: "Need Help Installing Citrix"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by Steve_79 on 2005-08-06
Hi All,

I need help i have downloaded citrix and installed it 
however i can not run the program it looks as if it is loading on the panel then nothing happens

Please help

Steve

---

### Post by myha on 2005-10-12
[QUOTE=Steve_79]Hi All,

I need help i have downloaded citrix and installed it 
however i can not run the program it looks as if it is loading on the panel then nothing happens

Please help

Steve[/QUOTE]
Hi!

I know its a bit late, but I had the same problem and I solved it...
All I had to do was ```
apt-get install libmotif3
```
And it worked...

Regards, Miha

---

### Post by Doctor HRH on 2005-10-12
Miha,

You're a genius!!

Thanks so much

HRH

---

### Post by Doctor HRH on 2005-10-12
Actually Miha, if you're still there

I can launch ICA Client but when I configure it with my work's settings, the OK button remains greyed out and I can't save the settings I've entered.

Any ideas?

HRH

---

### Post by myha on 2005-10-12
Hi!

Well I dont know what could the problem be... The only time I have OK grayed out is when I dont enter the server address/description under /network/server (not server location)...
Otherwise it works for me...

---

