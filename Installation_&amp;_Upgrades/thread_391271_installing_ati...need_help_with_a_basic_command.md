---
title: "installing ati...need help with a basic command"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by macm10 on 2007-03-23
hello i am following the steps to install the ati driver on:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a)

i am useing kubuntu 6.10 

when i type in:

gksudo gedit /etc/default/linux-restricted-modules-common

the bash shell doesnt seem to like gksudo or gedit very well.....

```
gksudo gedit /etc/default/linux-restricted-modules-common
```

and 

```
gksudo gedit /etc/default/linux-restricted-modules-common
```

are they typos? any help would go allong way.
thanks.

---

### Post by taurus on 2007-03-23
Gksudo gedit is for Gnome and since you are running Kubuntu, you should use

```
kdesu kate /etc/default/linux-restricted-modules-common
```

---

### Post by macm10 on 2007-03-23
thank you for helping me, the drivers worked out great

---

