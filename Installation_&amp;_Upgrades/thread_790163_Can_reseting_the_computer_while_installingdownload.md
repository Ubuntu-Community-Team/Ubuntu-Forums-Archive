---
title: "Can reseting the computer while installing/downloading with apt-get break your Linux?"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by Cifra on 2008-05-11
This is an interesting question...
I've got a few computers in school to setup by building them from the base upwards (don't ask why, I have a good reason to), but I would like to APT-GET, say X.org and let it download and install by itself (through the terminal with apt-get), and then leave and come back later, when it's done.

**The problem:**
What happens is that there's a possibility someone will get to the computer, think it's broken or something and do what every Windows user would: reset it...

now my question is, if the guy reset the computer during the download or during the install of the package, would he break the system? 

If not, can I just type the same command later and it would resume where it left off?

---

### Post by Yannick Le Saint kyncani on 2008-05-11
> **Cifra said:**
> What happens is that there's a possibility someone will get to the computer, think it's broken or something and do what every Windows user would: reset it...

Why don't you leave a big paper sign like to warn them not to touch it ?

> **Cifra said:**
> now my question is, if the guy reset the computer during the download or during the install of the package, would he break the system? 

If not, can I just type the same command later and it would resume where it left off?

During the install, yes, some packages would be left unconfigured, so :

- sudo dpkg --configure --pending
- sudo apt-get install --fix-broken
- retype the command and it will resume at a working point.

That's how I do it anyway.

---

### Post by Cifra on 2008-05-11
> **Yannick Le Saint kyncani said:**
> Why don't you leave a big paper sign like to warn them not to touch it ?

That would be like begging them do to just that :)

Thanks for your answer, I'll try using this method :)

---

### Post by Joeb454 on 2008-05-11
Also it may tell you to run 'dpkg configure -a' so just run ```
sudo dpkg configure -a
``` as well :)

---

