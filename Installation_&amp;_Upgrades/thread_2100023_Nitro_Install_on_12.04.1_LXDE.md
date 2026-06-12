---
title: "Nitro Install on 12.04.1 LXDE"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by TheFu on 2012-12-31
Just read an article [https://apps.ubuntu.com/cat/applications/precise/nitro/](https://apps.ubuntu.com/cat/applications/precise/nitro/) about a task manager called Nitro.  I'd like to try it, but can't find it under Synaptic.

I'm sure there is something trivial that I'm missing.
The system is running 12.04.1 x86 with LXDE.  No "Software Center".

$ sudo apt-get install nitro
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nitro

I searched inside Synaptic - nothing named "nitro" came up.
I googled and was directed back to the apps.ubuntu.com website.  
Looked for nitrotask and nitrotasks too. Nada.

Guess a PPA might be the only way?

---

### Post by vasa1 on 2012-12-31
> **TheFu said:**
> Just read an article [https://apps.ubuntu.com/cat/applications/precise/nitro/](https://apps.ubuntu.com/cat/applications/precise/nitro/) about a task manager called Nitro.  I'd like to try it, but can't find it under Synaptic.

I'm sure there is something trivial that I'm missing.
The system is running 12.04.1 x86 with LXDE.  No "Software Center"....
Maybe this is one of those things **only** available via the Ubuntu Software Center?

---

### Post by raja.genupula on 2012-12-31
I got Negative results with apt-cache search nitro but when I have opened its with my software centre it came up Buy product for $0.00 (free) .

As i know Lubuntu software centre not having that commercial product support.

---

### Post by TheFu on 2012-12-31
> **TheFu said:**
> 
The system is running 12.04.1 x86 with LXDE.  No "Software Center".
Guess a PPA might be the only way?

Found the PPA.
$ sudo add-apt-repository ppa:cooperjona/nitrotasks
$ sudo apt-get update
$ sudo apt-get install nitrotasks

That installed a few _unity_ cough, cough, things too. Oh well.
The app is installed and running.
v1.5 is under the** BSD license** according to the About popup.

Played with it for 5 minutes. This is a REALLY simplistic app for tasks.  At this point it is missing commonly used ideas for managing and adding new tasks.  Not what I needed. ```
sudo apt-get purge nitrotasks; sudo apt-get autoremove
``` 

```
 Removing libunity9 ...

```
Aaaah. I feel much better now.

---

