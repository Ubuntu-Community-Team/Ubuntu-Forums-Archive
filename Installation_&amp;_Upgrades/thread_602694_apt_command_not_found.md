---
title: "apt: command not found"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by sitha on 2007-11-04
Hi 
I am a newbie to ubuntu 7.04...I try to install some packages using following command:
sudo apt -get install XXXXXX

but it says following error:
sudo: apt: command not found

please somebody help me to overcome this trouble. Many thanks in advance.

Regards,
Sitha.

---

### Post by celettu on 2007-11-04
There's no space in "apt-get". One word.

```
sudo apt-get install <package>
```

or even better:

```
sudo aptitude install <package>
```

---

