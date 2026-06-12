---
title: "Installing VMWare onto ubuntu"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by aimhigher101 on 2008-01-28
I'm downloading VMWare and its giving me the choice of 2 type of downloads either VMWare in TAR Binary or VMWare in RPM Binary. 
Can anyone tell me what TAR and RPM mean and which one i will need for an ubuntu server?

---

### Post by zvacet on 2008-01-28
[tar](http://www.answers.com/tar+file?nafid=3)

[RPM](http://www.answers.com/rpm+?cat=health)

You need tar file.If you want to install vmware-server you don´t have to download it from Vmware site.You have it in synaptic.Only thing you will need is serial number.You can add this 92DFN-YWFF7-2C452-4TQCR.

---

### Post by aimhigher101 on 2008-01-28
yea i've tried the Tar file and its still unable to install for some reason i've managed to dwnload alien and perl so now i can dwnload rpm files but still im unable to install vmware. Btw ive installed vserver- debaintools is that like vmware (btw where do i go to, to run the application? cuz i cant find it) Dont know much about ubuntu so any advice would be much appreciated

thanks

---

### Post by zvacet on 2008-01-28
If you realy want to do it that way [here](http://www.howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10) are instructions.I belive it is easyer way to do it with synaptic.Make sure that you have all repos open.system>administration<software sources>chek all boxes under Ubuntu softwaer tab and under updates tab.Reload.After that 

```
gsudo gedit /etc/apt/sources.list
```

and add this at the bottom 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

Save and close the file.

```
sudo apt-get update
```

Now you have vmware-server in synaptic.Go and install it and all packages related to it.

---

### Post by aimhigher101 on 2008-01-29
it still doesn't seem to want to work is it because im trying to install it on ubuntu server 7.10? If so any help would be brilliant 
Btw i've tried what you said and still no luck :cry:

---

### Post by aimhigher101 on 2008-02-05
it works after changing ubuntu server to ubuntu workstation thanks a million dude :D

---

