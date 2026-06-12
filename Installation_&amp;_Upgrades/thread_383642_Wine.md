---
title: "Wine"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by ascus4 on 2007-03-13
I'm having a heckuvatime trying to figure out how to install software.

Is there a way to see if wine is installed?

Thanks,

---

### Post by Toadmund on 2007-03-13
I'm having a heckuva time installing wine for 64 bit, even this:
[http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit") doesn't seem to help:( 
I wish I could fix it because I'm tired of the reminders that it can't be found.

---

### Post by zvacet on 2007-03-13
Install it with synaptic.if it´s install allready you will see green box nex to wine in synaptic.To get it started in terminal type```
winecfg
```

---

### Post by ascus4 on 2007-03-13
I don't see it in Synaptic, installed or otherwise.  I used search.

---

### Post by Moeru on 2007-03-13
Seconding the earlier response. Open terminal and type winecfg. If this works, Wine is installed. You can even try running a program. In Terminal:

```
wine <program you want to run here>
```

---

### Post by zvacet on 2007-03-14
If you donn´t see it means it is not there.Open all repositories.Next is this
[http://www.winehq.com/site/download-deb]("http://www.winehq.com/site/download-deb")
or you can change your sources list 
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")
if you use Edgy and 
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")
if it is Dapper
After this search for wine in synaptic and mark it for install.

---

### Post by ascus4 on 2007-03-14
I'll give that a try.

Thank you.

---

### Post by ascus4 on 2007-03-14
Because I have a 64 bit AMD I have to install the hack.  Do I do this before or after I install wine?

Thanks,

W-

---

### Post by zvacet on 2007-03-14
[file://localhost/home/gianni/WineForAMD64]("file://localhost/home/gianni/WineForAMD64")

---

