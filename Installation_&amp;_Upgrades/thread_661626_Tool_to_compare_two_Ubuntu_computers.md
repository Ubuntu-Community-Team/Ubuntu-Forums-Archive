---
title: "Tool to compare two Ubuntu computers ?"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by ekh on 2008-01-08
Hi

I have a strange problem, and i suspect it is caused by a slightly different installation.

Is it possible to extract info about installed packages to a file, so I can make a diff between the two installations in an attempt to rtrack this down ?

PC1: Asus P5AD2 with Asus EN8600GT graphic card, 2.5GB ram 80GB HD
PC2: Medion MD40100 portable 0.5 GB ram 160 GB HD

Both machines are used for embedded development.

I have a small project in a SVN database, the project is checked out on both machines with RapidSVN.

I have used identical sources.list files and I have used identical commands to install wxWidgets 2.8.7.1-0 and Code::Blocks svn4771 on both machines.

My project compiles on both machines, but it only runs at the Medion.

Before some sw updates and installations, the program was running on both machines.

Debugger output on the Asus:

Starting debugger: 
done
Registered new type: wxString
Registered new type: STL String
Registered new type: STL Vector
Setting breakpoints
Debugger name and version: GNU gdb 6.6-debian
The program is not being run.
At /home/ekh/develop/conlog/PLC/sw/etq_user/etq_userApp.cpp:18
Debugger finished with status 0

Any ideas ?

---

### Post by tehet on 2008-01-08
Perhaps you could diff
```
dpkg --get-selections > mypackages
```
from both machines.

---

### Post by ekh on 2008-01-10
Thanks, it was just what I needed.

And the result from:

dpkg --get-selections > mypackages

Can be read in as markings in Synaptic Package Manager, so a setup can be replicated this way, if an identical installation is wanted on a new disk or an identical computer.

I like the possibility to edit the file to get exactly what's needed.

So your command line was the option I looked for in Synaptic. Thanks again :-)

Unfortunately I still have the debugger nut running, that is not solved yet.

---

### Post by ekh on 2008-01-18
The problem with the debugger was not caused by the installation.

I have a project for an arm processor debugging with OpenOCD and usbprog3.0.

The startup sequence for the debugger was put in the global debug settings in Code::Blocks instead of the project dependent debug setup. 

This worked fine for the arm, but when I later had to work on another project supposed to run on the PC, it was not happy to start as an arm processor.

Now the arm debugger setup is placed in the project specific properties, so all is OK now.

---

