---
title: "The following packages have unmet dependencies:  wine1.2 : Depends: libesd0 (&gt;= 0.2.3"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by shadow00 on 2011-01-06
Hello, i want to install wine to install FDM but i have this problem
Can you guys fix it for me ...?

```
kato@kato:~$ sudo apt-get install wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.2 : Depends: libesd0 (>= 0.2.35) but it is not installable
           Depends: libmpg123-0 (>= 1.6.2) but it is not installable
           Depends: libopenal1 but it is not installable
           Recommends: ttf-umefont but it is not installable
           Recommends: ttf-mscorefonts-installer but it is not installable
           Recommends: winbind but it is not installable
           Recommends: wine1.2-gecko but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not installable or
                       kdebase-runtime but it is not installable
E: Broken packages

```

---

### Post by dino99 on 2011-01-06
Latest wine is 1.3.10

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by shadow00 on 2011-01-06
> **dino99 said:**
> Latest wine is 1.3.10

[https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

thanks i'll try it

---

