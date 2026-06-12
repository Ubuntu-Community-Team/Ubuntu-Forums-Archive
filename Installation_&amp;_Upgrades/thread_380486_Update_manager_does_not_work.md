---
title: "Update manager does not work"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by kinemagician on 2007-03-09
a) I launched UPDATE MANAGER and I see there are 275 updates.
I click on the INSTALL UPDATES and nothing happens.

b) Then, I tried on a terminal

sudo apt-get update  ----  and the repositories are scanned

sudo apt-get install    (but again nothing happens)

The file /etc/apt/sources.list worked always fine....

What should I do to update my Feisty system?

Thanks,
Ettore

---

### Post by invalid on 2007-03-09
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kinemagician on 2007-03-10
Thank you very much. The commands you hinted allowed me to successfully update my Feisty.
What remains a mistery for me is why the UPDATE MANAGER did not worked properly.
Thank you again.
Ettore

---

### Post by manic34 on 2007-03-10
Hi Guys,

I am having the same problem that I cannot get any updates or open source material via Add/Remove. I tried your suggestion of :

sudo apt-get update
sudo apt-get upgrade

but to no avail, it tells me that it is connecting to the server but times out after sitting idle for 10+ minutes.

Do you know what may be causing this ?

Thanks,
Anthony

---

### Post by pradeepadapa on 2007-03-10
even i hav the same problm, no update is working on edgy eft...........

anyone has a solution to this problem, 

even add/remove update not working, software sources update also not working,

**does anyone know**   ?????????????????????????/

---

