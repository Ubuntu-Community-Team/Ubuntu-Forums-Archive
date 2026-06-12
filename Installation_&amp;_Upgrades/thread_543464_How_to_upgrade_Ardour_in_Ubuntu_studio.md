---
title: "How to upgrade Ardour in Ubuntu studio"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by kimodk on 2007-09-05
Hi!
I try to update Ardour to version 2.05 from getdeb, but the installer says later version installed and wont give me permission to install.

Can anybody help?

Thx Kimo.

---

### Post by saintj0n on 2007-09-23
Can you cut and paste the output when you do this or take a screenshot and upload it?  Also, did you type sudo and use chown to set up ownership? 
sudo will give you permission to give yourself access to whatever you want. chown will allow you to continue to have access without being root....

Hope this helps!

---

### Post by SoundFlame on 2008-03-07
hi all new version of Ardour is released 2.3
can u tell me how to updete 

yeah i'm noob

---

### Post by zvacet on 2008-03-07
Type in terminal

```
gksudo gedit /etc/apt/sources.list
```

add this line

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

save and close file

```
sudo apt-get update
```

---

