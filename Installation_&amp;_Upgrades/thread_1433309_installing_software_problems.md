---
title: "installing software problems"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by slider1987 on 2010-03-18
i am trying to install World of warcraft on to my computer.  When i went to install the software needed it told me to wait for software manager to quit.  I do not have any other software running or downloading.  Any ideas on where i have gone wrong

thanks for any help possible

---

### Post by overlord.gaurav on 2010-03-18
I guess you're trying to install 'the software' from the terminal. And in that case, you must have left the 'Synaptic Package Manager' open or the 'Add/Remove' application open. Close either/both of them.

---

### Post by slider1987 on 2010-03-18
i get this report when i try to even go into synaptic package manager

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by n0dix on 2010-03-18
Do: sudo dpkg --configure -a

---

### Post by slider1987 on 2010-03-18
i dont know how to.  can you explain it

---

### Post by n0dix on 2010-03-18
In console execute: sudo dpkg --configure -a.

To open one:
Press Alt+F2, then write xterm, press Enter

---

### Post by overlord.gaurav on 2010-03-19
> **slider1987 said:**
> i dont know how to.  can you explain it

> **n0dix said:**
> In console execute: sudo dpkg --configure -a.

To open one:
Press Alt+F2, then write xterm, press Enter

Or use a simple graphical manner: Click on Applications -> Accessories -> Terminal
Enter the following: 
```

sudo dpkg --configure -a

```

---

