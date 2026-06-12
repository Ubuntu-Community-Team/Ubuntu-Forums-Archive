---
title: "Package Manager broken"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by STUMPOFWAR on 2007-07-13
OK, my package manager is broken. I tried to get the new OpenOffice updates and I got this error when I put my cursor over the little orange square telling me updates are available

```
Error: BrokenCount >0
```

When I open package manager I get this error:

```
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

So I run that:

```
seliason@Teletran-1:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

So I run dpkg and.....
```

seliason@Teletran-1:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
```

I have no idea what "superuser privelage" is so I decide to try Synaptic....and I get
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

which brings me back to the superuser issue..... any thoughts?

---

### Post by STUMPOFWAR on 2007-07-13
Also......FYI this is on a PPC machine........

---

### Post by Pumalite on 2007-07-13
Try: sudo dpkg --configure -a
If not, try: sudo su

---

### Post by refusejesus on 2007-07-13
yep i'm having the same problems ever since the openoffice updates, its affecting synaptic with the smae error message

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

It seems to be also affecting installing otherp rograms using other installers such as automatix

> !!SCRIPT OUTPUT END!!
[07/13/2007 - 15:53.13] - ERRORS OR WARNINGS WHERE REPORTED
[07/13/2007 - 15:53.13] - FATAL - Gdesklets - An apt-based error occurred and installation was unsuccessful
[07/13/2007 - 15:58.39] - !!Starting Automatix 1.1-4.11!!
[07/13/2007 - 15:58.52] - !!SCRIPT OUTPUT START!!
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by refusejesus on 2007-07-18
Anyone have any ideas?

---

### Post by davidjmayo on 2007-07-18
> **Pumalite said:**
> Try: sudo dpkg --configure -a
If not, try: sudo su

did you run from a terminal (applications==>accessories==>terminal)
```
sudo dpkg --configure -a
```

BTW when it asks for a password it is your login password

---

