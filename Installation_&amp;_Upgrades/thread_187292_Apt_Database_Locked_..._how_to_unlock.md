---
title: "Apt Database Locked ... how to unlock????"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by mexlinux on 2006-06-02
Hi:
Soething went wrong installing sun-java
Now I can not use apt, because datbase is locked...!!!

How to unlock it??????

Thanks,

---

### Post by kimastergeorge on 2006-06-02
If you have synaptic (or whatever the Kubuntu equivalent is) open, close it. If you have another instance of apt-get running, stop it or wait for it to stop. If you have the update manager open, close it.

Then try installing again. It should work now.

---

### Post by 5-HT on 2006-06-02
Best thing to try is a reboot.
If that doesn't help and apt/dpkg are not running, you can try removing the lock file:
```
 sudo rm /var/cache/apt/archives/lock 
```

Hope that helps.

---

### Post by mexlinux on 2006-06-02
Nothigh worked but this:

sudo dpkg --configure -a

---

