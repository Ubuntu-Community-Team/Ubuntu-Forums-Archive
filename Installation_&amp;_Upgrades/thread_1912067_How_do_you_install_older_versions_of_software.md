---
title: "How do you install older versions of software"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by davethewave83 on 2012-01-19
I'm running Empathy 2.30.3 on Ubuntu 10.04 (Lucid Lynx) 
and Empathy 3.2.0.1 on Ubuntu 11.10 (Oneiric) 

Empathy 2.3 has file transfer support
Empathy 3.2 has file transfer greyed out

I would like to install 2.3 in oneiric ocelot.

I edit the sources.list and commented out all sources and then added the repo for Lucid, hit refresh on synaptic but, it still reported 3.2.0.1 as being the only version available.

---

### Post by UltimateCat on 2012-01-19
Open a terminal or Control> Alt> T

```
]apt-get install <nameofpackage>

```

I learned directly from a  Linux Rep. that if you are running a server with no GUI than you can not use Synaptic Pkg Mgr.

[www.linuxquestions.org/questions/linux-newbie](www.linuxquestions.org/questions/linux-newbie)

Hope this helps

---

### Post by davethewave83 on 2012-01-20
> **UltimateCat said:**
> Open a terminal or Control> Alt> T

```
]apt-get install <nameofpackage>

```

I learned directly from a  Linux Rep. that if you are running a server with no GUI than you can not use Synaptic Pkg Mgr.

[www.linuxquestions.org/questions/linux-newbie](www.linuxquestions.org/questions/linux-newbie)

Hope this helps

Thanks for the reply, but apt-get install empathy will just install the latest version won't it? I would like to install the older version.

---

### Post by raja.genupula on 2012-01-20
From the cache folder of the 10.04 get the empathy files and put them in a folder and do the installation 

```
sudo dpkg -i <here plakce that name>.deb
```

if you got any dependencies problem look them at the synaptic package manager and install them from there and try again the above commands .

All the best .

---

### Post by davethewave83 on 2012-01-20
> **raja.genupula said:**
> From the cache folder of the 10.04 get the empathy files and put them in a folder and do the installation 

```
sudo dpkg -i <here plakce that name>.deb
```

if you got any dependencies problem look them at the synaptic package manager and install them from there and try again the above commands .

All the best .

this might work, but I don't think so as the 10.04 package is amd64, and the oneiric OS is 32 bit. 

worth a shot though, I'll try it tomorrow.

---

### Post by raja.genupula on 2012-01-20
ok then download empathy from the ubuntu packages 
[http://packages.ubuntu.com/lucid/empathy](http://packages.ubuntu.com/lucid/empathy)

install it , get the required dependencies from synaptic . 

all the best

---

