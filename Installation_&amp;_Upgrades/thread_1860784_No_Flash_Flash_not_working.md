---
title: "No Flash/ Flash not working"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by chinnerz on 2011-10-15
So i did the update this morning, using the automatic update thingo which popped up. 
It seems to be working alright, but i cant seem to be able to use flash. I am using Chrome, but i have also tried firefox... to no avail

I have installed flash player 10 and the flash plug in, and have tried re installing them a few times using the software center.

any help is much appreciated.  

more info about my build:
Release 11.10(oneiric) -- X64
Kernel Linux 3.0.0-12-generic
Gnome 3.2.0

4gb ram
intel U7300 ULV cpu.

---

### Post by elgrodo on 2011-10-15
I have the same problem

---

### Post by chinnerz on 2011-10-15
i just realized after i install it, there isn't a tick on the icon which appears when something is installed.

I have tried it using the synaptic package manager.. still not working.

---

### Post by chinnerz on 2011-10-15
OK i fixed it!!

to any one else who is having the same problem:
open up the synaptic package manager, 
up the top there is a text field named filter,
type "flash"
this will bring up anything with the word flash in it... obviously :)
close to the top (for me, it may not be in the same place for you) you will see something called flashplugin-installer. the version is 11.0.1.152ubuntu1, 
mark this for instillation by clicking the check box.
you should see that two files are to be removed, this is ok.
up the top there is an icon with a big tick in it called apply. 
click this
and that was problem solved for me.

hope that helps.

---

### Post by elgrodo on 2011-10-15
thanks, works perfectly now

---

