---
title: "[SOLVED] Can't install or uninstall any more packages!!"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by 2uRcJQ34G1 on 2008-08-20
Hello,
I am new to Ubuntu and its great, except I've run into an obstacle. I cannot Install or Uninstall any more packages neither through 'Add/Remove Applications' nor through 'Synaptic Package Manager'. When I open SPM, get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

As I searched the forums for this error I came across a possible solution: To clear the cache in terminal. So I did:

sudo apt-get clean (This worked)
sudo apt-get autoclean
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

The problem still persists, can someone help me with this?
Thank You.

---

### Post by cpetercarter on 2008-08-20
Open a terminal (Applications > Accessories > terminal).

Type in

```
sudo dpkg --configure -a
```

You will be asked for your password. Just type it in and press enter - you will not see either your password or a line of dots or asterisks on the terminal screen - don't worry, this is normal.

The dpkg programme will then output a load of stuff to the terminal, which will (hopefully) tell you that it has sorted the problem.

---

### Post by 2uRcJQ34G1 on 2008-08-20
Hi,
I did and it gave me this...

(All kinds of files)...
...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 kde4libs-bin
 kdebase-runtime-bin-kde4

Thanks for the reply. What now?

---

### Post by oldos2er on 2008-08-20
Try running "sudo aptitude install -f"

---

### Post by loboc on 2008-08-20
you are done problem solved 
try 

```
apt-get update
```


 
and see if synaptic works to verify

---

### Post by 2uRcJQ34G1 on 2008-08-20
Hi, thank you all!! Ubuntu Forums RoCk!!
This how I did it, for others who might have the same problem. I tried to run the updater and it started the manager for me. After which I just filter the broken packages and then re-installed those. Later, I completely un-installed the packages which I was trying to uninstall (this is what where the trouble started). Et voila! Probleme solved. Cheers.

---

