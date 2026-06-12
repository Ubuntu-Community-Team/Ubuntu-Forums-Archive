---
title: "unable to install skype on 12.10"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by proggrammer on 2012-12-04
Hi, I am using 12.10.

When I am doing:

$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype

---

### Post by kleenex on 2012-12-04
Hi **proggrammer**, please try to add a archive cannonical repository or try to download Skype from official site: [COLOR=RoyalBlue][http://www.skype.com/intl/en/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en/get-skype/on-your-computer/linux/)[/COLOR]
```
$ sudo add-apt-repository "deb http://archive.canonical.com/$(lsb_release -sc) partner"
$ sudo apt-get update 
$ sudo apt-get install skype
```

---

### Post by proggrammer on 2012-12-05
user@computer:~$ sudo add-apt-repository "deb http://archive.canonical.com/$(lsb_release -sc) partner"
[sudo] password for user: 
user@computer:~$ sudo apt-get update
E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
caps@tesseract:~$

---

### Post by kleenex on 2012-12-05
Hi, please show your [COLOR=SeaGreen]/etc/apt/sources.list[/COLOR] file. Something on line 61 is wrong. One more thing; also show [COLOR=Blue]lsb_release -sc[/COLOR] command result. Did you tried to download Skype from official website?

Wait! Try once again to run [COLOR=Blue]add-apt-repository [COLOR=Black]command, but with space after [/COLOR][/COLOR]archive.canonical.com/, so

```
$ sudo add-apt-repository "deb http://archive.canonical.com/[COLOR=Red]spacebar_here [/COLOR]$(lsb_release -sc) partner" 
$ sudo apt-get update  
$ sudo apt-get install skype
```

An example for Ubuntu 12.04
```
deb http://en.archive.ubuntu.com/ubuntu/ precise main restricted
```

---

### Post by zvacet on 2012-12-05
```
cat /etc/apt/sources.list
```

and post output here to see what is wrong in it.

---

