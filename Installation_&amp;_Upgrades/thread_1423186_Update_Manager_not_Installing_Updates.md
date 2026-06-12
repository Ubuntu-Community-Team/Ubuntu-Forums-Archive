---
title: "Update Manager not Installing Updates"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2010-03-06
I recently upgraded to 9.04 and Update Manager stopped working. 

If I start Update Manager it will check for updates and display them but will not install the updates. I am prompted for a password but the updates are never downloaded and I get no error messages. 

Synaptic does the same thing.

'sudo synaptic' works

apt-get works as expected.

---

### Post by akand074 on 2010-03-06
I think that has happened to me before.. I can't remember what I did to fix it. I think it was a matter of a simple restart. I think I actually had updated to a new kernel and not booted into it yet, and when I restarted and booted to it and did an update from there it worked. Though that's off blurred memory from long ago. That is as much help as I can be sorry !

---

### Post by MelDJ on 2010-03-06
try terminal 
```
sudo apt-get upgrade
```

---

### Post by rsteinmetz70112 on 2010-03-06
I have restarted and that didn't fix it.

---

### Post by rsteinmetz70112 on 2010-03-06
That works but I want to fix the problme.

---

### Post by MelDJ on 2010-03-06
> **rsteinmetz70112 said:**
> That works but I want to fix the problme.

did it upgrade the packages?
have you tried opening update manager now?

---

### Post by wojox on 2010-03-06
Did it download everything from MelDJ's post. In other words it didn't say <some number> not upgraded at the end ?

---

### Post by rsteinmetz70112 on 2010-06-16
It never did download anything. There are some problems with pam, I'm working on them.

---

