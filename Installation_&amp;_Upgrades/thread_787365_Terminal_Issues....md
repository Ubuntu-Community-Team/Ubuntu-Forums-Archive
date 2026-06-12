---
title: "Terminal Issues..."
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by brett11808 on 2008-05-08
So I've had my fair share of mishaps with terminal commands but this one is the worst so far...
I am trying to install Glabels and the first time i used synaptic package manager and everything worked perfectly except that i couldn't print my labels. So after screwing everything up with terminal commands given to me from a so called reliable source my whole system was ruined and not knowing how to fix it i have started with a fresh install of 8.04. 
So this time i used the following that i got from...

[http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron]("http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron")

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
```
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get install glabels
```

and this is the output
```
brett@brett-laptop:~$ sudo apt-get install glabels
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

```

so can someone help me fix this????? 
Thanks for any help!

---

### Post by Partyboi2 on 2008-05-08
can you post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by oldos2er on 2008-05-08
Please post the output of "cat /etc/apt/sources.list.d/medibuntu.list"

---

### Post by brett11808 on 2008-05-09
Ok never mind guys I couldn't get Ubuntu to boot at all so I just started with another fresh install.  Thanks for the speedy responses!!

---

