---
title: "cannot install ubuntu tweak"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by yaron86 on 2010-12-26
Hi there, I am trying to install ubuntu tweak, but the deb package says error:
Error: Dependency is not satisfiable: gconf2 (>= 2.28.1-2)
I tried going to synaptic and reinstall the gconf2, but still the same error.

---

### Post by dino99 on 2010-12-26
where did you get that "ubuntu tweak" ?

clean the cache:

sudo rm /var/cache/apt/archives/*

then update

---

### Post by Frogs Hair on 2010-12-26
What version of Ubuntu ? Ubuntu Tweak may no longer work with anything prior to 9.10. [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by karthick87 on 2010-12-26
```
sudo add-apt-repository ppa:tualatrix/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install ubuntu-tweak
```

---

### Post by yaron86 on 2010-12-26
> **karthick87 said:**
> ```
sudo add-apt-repository ppa:tualatrix/ppa
``````
sudo apt-get update
``````
sudo apt-get install ubuntu-tweak
```


Thank you very much! it worked! :)

---

### Post by Saudffs on 2010-12-26
Had the same problem but karthick87's solution worked perfectly for me on Ubuntu 10.04 64 bit, thank you both. BTW you should mark this as solved so people can find this faster.

---

### Post by chinamike on 2011-07-31
> **karthick87 said:**
> ```
sudo add-apt-repository ppa:tualatrix/ppa
``````
sudo apt-get update
``````
sudo apt-get install ubuntu-tweak
```

thanks  Karthick87! I tried that  sudo rm /var/cache/apt/archives/* by dino99, but it said it couldn't because of a "partial" directory? or similar...so your thing worked!

Oh, and I'm using Lucid 10.04.3

---

