---
title: "could I Install new program without update the current packages ?"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by forsubhi on 2012-09-25
[B][SIZE=2]I read this instructions to install openbravo [/SIZE]
  [/B]

```
**Installation **

 **  Command line installation using PPA Repository **

 
[LIST]
[*] Enable the openbravo-isv PPA Repository:
[/LIST]
 sudo add-apt-repository ppa:openbravo-isv/ppa  
[LIST]
[*] Update the package tree and perform the install:
[/LIST]
 $ sudo apt-get update $ sudo apt-get install openbravo-3  Note: sudo command will ask for the user password. 

```

but my updates is 1000 gb so I don't want to update my all packages and my dsl is 256 so it will take a lot of time to complete the updates , could I install openbravo without update ?

---

### Post by akoskm on 2012-09-25
Sure!
```

sudo apt-get update

```
will only update the *index* of available packages, it won't actually download any package:

From apt-get manual:
> 
update
[INDENT]update is used to resynchronize the package index files from their sources. The indexes of available packages are fetched from the location(s) specified in /etc/apt/sources.list.[/INDENT]


---

### Post by forsubhi on 2012-09-25
thank you man .. I now know the fact of the instruction >:lolflag:

but my slow internet connection confused me  ):P

---

