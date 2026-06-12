---
title: "apt-get update doesn't work"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by abtekk on 2011-10-29
Hi guys, none of my repo's are working, I have just done a fresh install of Lubuntu 11.10 and synaptic package manager won't search for packages, update manager has no updates and running sudo apt-get update just kicks out:

```


lewis@lewis-AOD255:~$ sudo apt-get update
[sudo] password for lewis: 
Reading package lists... Done
lewis@lewis-AOD255:~$ 

```

---

### Post by 2F4U on 2011-10-29
What mirror are you using? Maybe a switch to the main mirror helps.

---

### Post by dino99 on 2011-10-29
how is your /etc/apt/sources.list ?

be sure that these archives (main, universe, multiverse, proposed) are activated into synaptic

---

### Post by abtekk on 2011-10-29
> **dino99 said:**
> how is yout /etc/apt/sources.list ?

be sure that these archives (main, universe, multiverse, proposed) are activated into synaptic

LOL! My sources.list is empty.... God dammit.

---

### Post by drs305 on 2011-10-29
Open Software Sources/Synaptic and take a look at your repository list. Are the repositories enabled?
From a terminal, you can see the active repositories in sources.list with:
```
grep -v '#' /etc/apt/sources.list

```
Also try another server.

---

### Post by abtekk on 2011-10-29
> **drs305 said:**
> Open Software Sources/Synaptic and take a look at your repository list. Are the repositories enabled?
From a terminal, you can see the active repositories in sources.list with:
```
grep -v '#' /etc/apt/sources.list

```
Also try another server.

```

grep: /etc/apt/sources.list: No such file or directory

```

Did something go wrong in the install?

---

### Post by drs305 on 2011-10-29
Don't know what happened but you can generate a new one from this site:
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

---

### Post by abtekk on 2011-10-29
> **drs305 said:**
> Don't know what happened but you can generate a new one from this site:
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

It's alive! Thank you sir.

---

