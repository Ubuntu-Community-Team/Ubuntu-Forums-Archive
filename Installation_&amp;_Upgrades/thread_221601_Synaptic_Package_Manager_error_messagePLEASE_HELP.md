---
title: "Synaptic Package Manager error messagePLEASE HELP"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by ootd on 2006-07-23
Every time I open Add or Remove programs and try to install something it give me this:

E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2 No such file or directory)

this also happens when I just open the synaptic package manager itself. 

help would be much appreciated

---

### Post by xXx 0wn3d xXx on 2006-07-23
> **ootd said:**
> Every time I open Add or Remove programs and try to install something it give me this:

E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2 No such file or directory)

this also happens when I just open the synaptic package manager itself. 

help would be much appreciated

Are you running Synaptic as root ? Try running this in terminal:
> gksudo synaptic

---

### Post by ootd on 2006-07-23
attached a screenshot of it

---

### Post by ootd on 2006-07-23
> **xXx 0wn3d xXx said:**
> Are you running Synaptic as root ? Try running this in terminal:


no it brings up the same window

---

### Post by chimastafunk on 2007-01-03
I just resolved this problem for myself. The issue was that my /root directory had been corrupted somehow. It was reading as type ? instead of d in ls. I renamed it 'rootbk' and created a new /root folder, and everything worked fine again. Still trying to figure how it happened in the first place

---

