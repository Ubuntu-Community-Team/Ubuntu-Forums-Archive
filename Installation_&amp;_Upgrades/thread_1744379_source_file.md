---
title: "source file"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by sameerkof on 2011-04-30
Hello
source file 
was adding screenlets and this happened :D
using 11.04

E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/screenlets-ppa-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Any solutions ?

---

### Post by plucky on 2011-04-30
> **sameerkof said:**
> Hello
source file 
was adding screenlets and this happened :D
using 11.04

E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/screenlets-ppa-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Any solutions ?

Post from a terminal ```
cat /etc/apt/sources.list.d/screenlets-ppa-natty.list
```

---

### Post by matt_symes on 2011-04-30
Hi

Open a terminal and copy and paste

```
cat /etc/apt/sources.list.d/screenlets-ppa-natty.list
```

Copy and paste the output back here.

EDIT:

@plucky. Beaten to it. Please, this is yours :D

Kind regards

---

### Post by sameerkof on 2011-04-30
> **plucky said:**
> Post from a terminal ```
cat /etc/apt/sources.list.d/screenlets-ppa-natty.list
```


nothing happen after runing this cmd still update manager giving this error 
'E:Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/screenlets-ppa-natty.list'

---

### Post by sameerkof on 2011-04-30
> **matt_symes said:**
> Hi

Open a terminal and copy and paste

```
cat /etc/apt/sources.list.d/screenlets-ppa-natty.list
```Copy and paste the output back here.

EDIT:

@plucky. Beaten to it. Please, this is yours :D

Kind regards

[SIZE=3]output
[/SIZE]
[SIZE=3]sameerkof@ubuntu:~$ cat /etc/apt/sources.list.d/screenlets-ppa-natty.list
ain
sameerkof@ubuntu:~$ [/SIZE]

---

### Post by sameerkof on 2011-04-30
sudo apt-add-repository ppa:screenlets/ppa 
 sudo apt-get update
 i just run these to cmds in terminal and everything gets back to normal.


 **thanks for helping :)** :popcorn:

---

