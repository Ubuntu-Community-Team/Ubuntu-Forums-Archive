---
title: "Install G-pen F350 genius on Ubuntu 10.10"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by AlfredoMCaceres on 2011-02-07
Hi everybody....
I wanna to install digital tablet genius g-pen F350 on ubuntu maverick 10.10 , ubuntu runs very well, and  i do not problems, but i  could not install that tablet....please  help me...

---

### Post by Favux on 2011-02-07
Hi AlfredoMCaceres,

Welcome to Ubuntu forums!

First let's find out what driver the G-pen F350 is suppose to use.  Enter in a terminal:
```
lsusb
```
and post the line that has your tablet in it.

---

### Post by AlfredoMCaceres on 2011-02-07
> **Favux said:**
> Hi AlfredoMCaceres,

Welcome to Ubuntu forums!

First let's find out what driver the G-pen F350 is suppose to use.  Enter in a terminal:
```
lsusb
```and post the line that has your tablet in it.
Hi this the line:

alfredo@alfredo-desktop:~$  lsusb
[COLOR=DeepSkyBlue]Bus 003 Device 002: ID 172f:0032 Waltop International Corp. [/COLOR]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub   

and thanks..by your response...:p

---

### Post by Favux on 2011-02-07
Hi Alfredo,

Sure, not a problem.  You have a rebranded Waltop tablet.  See the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1") to set it up.

---

