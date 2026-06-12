---
title: "Panic-Desperated-Help me"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-08-20
I have uninstalled mono by removing some selected file using Sympatic package Manager, the problem is now when I tried to run Sympatic Package Manager I get the following error"failed to execute child proess gksu" no such file or directory, and my update manager has desapeared from system/administration.
I am very desperated

---

### Post by crazyness003 on 2008-08-20
have you tried running 
```
sudo aptitude
```Its the Synaptic equivalent for CLI. See if that works, and Im sure if it does work, the problem would be less intense

If this works then try to re-install Synaptic. You can do searches in Aptitude by pressing F10 -> Search -> Find

---

### Post by hoboy on 2008-08-20
> **crazyness003 said:**
> have you tried running 
```
sudo aptitude
```Its the Synaptic equivalent for CLI. See if that works, and Im sure if it does work, the problem would be less intense

Thanks but when I follow your advice it stop at waiting for headers
at total progress  97%

---

### Post by crazyness003 on 2008-08-20
Try to re-install using apt-get, it seems easier.
but, I think all you're missing is gksu. Try this
```
sudo apt-get install gksu
```Im shooting blindly here, so im trying to help you to the best of my abilities.

---

