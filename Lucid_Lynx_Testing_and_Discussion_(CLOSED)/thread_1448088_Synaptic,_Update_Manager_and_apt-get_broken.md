---
title: "Synaptic, Update Manager and apt-get broken?"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by imacQ on 2010-04-06
After running "apt-get -f install" I was finally able to successfully run Update Manager which completed with no errors. Everything seemed to work fine. However, upon reboot all update avenues fail, and Apport crashes?

> ```
linux@linux-laptop:~$ sudo apt-get -f install
[sudo] password for linux: 
Reading package lists... Done
Bus error (core dumped)e... 0%
```


System = Acer Aspire 5315-2077 dual boot with XP Pro.

Any solutions/suggestions would be greatly appreciated.

---

### Post by dino99 on 2010-04-06
is there a crash into /var/crash, if so report it (double click)

you are posting against Lucid: is it a fresh install ? a dist-upgrade ?
do you have third party repo / ppa ?

first clean your system then reboot

---

### Post by byStanderone on 2010-04-06
hi, 
...a bit curious about the apt-get -f install line on the OP, is that a legit apt-get line or a typo? hope a sudo apt-get autoclean would do.

---

### Post by ratcheer on 2010-04-06
Will it work with the -q option?

Tim

---

### Post by Uncle Spellbinder on 2010-04-06
> **byStanderone said:**
> hi, 
...a bit curious about the apt-get -f install line on the OP, is that a legit apt-get line or a typo?

I thought it was suppose to be *sudo apt-get install -f*

---

### Post by imacQ on 2010-04-06
Thanks dino99. 

Machine has a clean a install of 10.04 Beta. 

Synaptic, apt and Update all alright after starting up in recovery mode and running autoclean and -f install through console (twice starting in recovery). Exited console with gdm start and was able to use Update Manager to install updates. On restart after running Synaptic the updating tools broken again. Recovery mode start again and all appears ok with updating. However, other applications issues are cropping up, but that should be a new post.

---

