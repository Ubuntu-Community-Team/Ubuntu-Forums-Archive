---
title: "install refused due to legacy package?"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by prue on 2010-04-17
Hello,
Trying to install Wine on 9.10 Kubuntu and gets almost there and fails on:
"Cannot get the exclusive lock on the packaging backend
Please close any other legacy packaging tools that may be open"

I haven't got anything else running.  Not even sure what the install program is - its just called KpackageKit.

Also not sure how to pick the right program to download - lot of similar names came up on the search.

THank you
Prue

---

### Post by byStanderone on 2010-04-17
...haven't tried kubuntu yet, but when it comes to downloading packages, the safest way is from a legitimate site...such as kubuntu.org itself.

---

### Post by tom4everitt on 2010-04-17
Try to install wine from terminal instead. Simply run:

sudo apt-get install wine1.2

in a terminal.

---

### Post by prue on 2010-04-17
> **tom4everitt said:**
> Try to install wine from terminal instead. Simply run:

sudo apt-get install wine1.2

in a terminal.

Hi Tom,
Tried that, answer=  
  E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
me@ubuntu:~$

BUT - an earlier attempt at installing Google Earth seems to have repeated .... ???

Cheers?

---

### Post by tom4everitt on 2010-04-18
What do you mean happened with the earlier attempt to install google earth?

In linux only one application is able to install programs/updates at the time (to avoid system corruption etc.) Could it be that you have some other applications open that handles packages in some way? A window/applet with updates waiting to be installed for example. Or that you didn't close the program you normally install applications with before running the command I suggested.

---

### Post by prue on 2010-04-19
> **tom4everitt said:**
> What do you mean happened with the earlier attempt to install google earth?
.

Hi Tom,
It simply failed to complete. 
UNfortunately, linux is not really easy to get around in and I have not found any of my old helpful Windoze utilities equivalents. 
I can't find  any way of being sure of what programs are running, installed, or how to.

I want to install Wine - altho I THOUGHT it was in Kubuntu by default. 
I did apparently do things ok with your suggestion but there is something jamming the system.
Still is after 12 hours and two reboots.

Cheers?

---

