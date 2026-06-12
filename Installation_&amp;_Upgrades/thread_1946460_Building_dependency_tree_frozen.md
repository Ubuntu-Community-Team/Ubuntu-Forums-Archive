---
title: "Building dependency tree frozen"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by 3DTOPO on 2012-03-24
HI,

After trying to install Wine 1.3 with apt-get on Ubuntu 1.3 every time I try to run apt-get now it is stuck at "Building dependency tree... 50%".

I have searched the forms and searched Google but can't seem to find anything relevant.

Also if I run:

sudo dpkg --configure wine1.3

I get: 

dpkg: dependency problems prevent configuration of wine1.3:
 wine1.3 depends on libmpg123-0 (>= 1.6.2); however:
  Package libmpg123-0 is not configured yet.
 wine1.3 depends on libopenal1; however:
  Package libopenal1 is not configured yet.
dpkg: error processing wine1.3 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine1.3

I am new to Ubuntu and would greatly appreciate any suggestions, thanks!

---

### Post by raja.genupula on 2012-03-24
Hi that two dependencies installed or not , check by using synaptic pkg manager . 
if its saying installed then  un install and re install them .

try again by installing wine again 1

---

### Post by 3DTOPO on 2012-03-25
Hi Raja,

The problem is I cannot use synaptic pkg manager because it can't build the dependency tree either.

It gets stuck at 50% too with the same message:

"Building dependency tree".

Thanks for your help though.

---

### Post by raja.genupula on 2012-03-26
what you got if you did this 
```
sudo apt-get install -f
```

---

### Post by ncheikh25 on 2012-05-11
You can try running "sudo apt-get update"

---

