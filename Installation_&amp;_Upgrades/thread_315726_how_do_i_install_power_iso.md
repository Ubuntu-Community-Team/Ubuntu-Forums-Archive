---
title: "how do i install power iso?"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by madhatter434343 on 2006-12-09
im running edgy and am extremely new to ubuntu so this stuff is really confusing. i have downloaded poweriso from the website and extracted it but im not sure how to install it. i need to becuase i want to burn a .daa file to a disc. thank you in advance

---

### Post by kane77 on 2006-12-09
you need to download tool called poweriso...
```
$ wget http://poweriso.com/poweriso.tar.gz
$ tar -zxvf poweriso.tar.gz
```

---

### Post by nousefreak on 2008-03-03
the above sollution works fine, but is may be more functional if you do the following:

```
$ wget http://poweriso.com/poweriso.tar.gz
$ sudo tar -zxvf poweriso.tar.gz -C /bin
$ rm -f poweriso.tar.gz
```

Now you can call the program from every location just by typing 
```
poweriso
```

---

### Post by Pumalite on 2008-03-03
[http://linux.softpedia.com/get/Multimedia/Audio/AcetoneISO-16724.shtml](http://linux.softpedia.com/get/Multimedia/Audio/AcetoneISO-16724.shtml)

---

### Post by bulletxt on 2008-03-04
wow that is a very old version of AcetoneISO!

install latest 2.0.1 in qt4!

---

### Post by SloYerRoll on 2008-03-09
> **nousefreak said:**
> the above sollution works fine, but is may be more functional if you do the following:

```
$ wget http://poweriso.com/poweriso.tar.gz
$ sudo tar -zxvf poweriso.tar.gz -C /bin
$ rm -f poweriso.tar.gz
```

Now you can call the program from every location just by typing 
```
poweriso
```Thanks for your post!
I'd been looking around for solutions. This looks to be the best one (to me). 

Cheers,

---

