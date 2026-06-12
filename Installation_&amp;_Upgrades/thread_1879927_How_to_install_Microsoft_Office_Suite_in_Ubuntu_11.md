---
title: "How to install Microsoft Office Suite in Ubuntu 11.10"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by lrs52200 on 2011-11-12
I am running Ubuntu 11.10 and need to install Microsoft's Excel program - when I right click the "setup.exe" file receive the error message that the file is not marked executable.

I have WINE installed, but do not know how to change the file permissions for MS Office Suite -

Can you take me through the process, step by step?

Thank you.:confused:

---

### Post by darkod on 2011-11-12
And you can't use the Libre Office software included in Ubuntu? It can open most Office files unless you have some "special" features.
Have you investigated whether the version of Office you are trying is compatible with wine at all? Has someone successfully installed it?
You are aware that wine doesn't automatically cover all windows software right?

---

### Post by boblizar on 2011-11-12
build up a virtual machine of windows xp......

virtual box

mount windows iso

install as if installing to a blank hardware pc

mount office iso / install

samba / http / ftp / share a folder to transport documents back and forth.  id rather use gedit / open office / libra office

---

### Post by batharoy on 2011-11-12
> **boblizar said:**
> build up a virtual machine of windows xp......

virtual box

mount windows iso

install as if installing to a blank hardware pc

mount office iso / install

samba / http / ftp / share a folder to transport documents back and forth.  id rather use gedit / open office / libra office
Although this is probably the best way to run windows programs, the easy way to make the file in question executable is to 
right click
properties
select permissions tab
check the box next to "Allow executing file as program".

---

### Post by lrs52200 on 2011-11-12
Darkod-  Sadly, I cannot use another program - it must be MS Excel.

Boblizar - I have no idea how to proceed with your instructions (very much a newbie)

Batharoy - I tried to change permissions as you said, but no matter what I do I get this error message: "The permissions could not be changed. Sorry, could not change the permissions of "setup.exe": Error setting permissions:  Read-only file system"

When I click "Read and Write" Access for Owner, the error message simply repeats itself.

---

### Post by lrs52200 on 2011-11-12
SUCCESS!!!

I opened a terminal, typed "wine" with a space after it and then drag/dropped the .exe onto the terminal.

yea!!!  I'm so happy!!!

---

### Post by boblizar on 2011-11-15
alt + f2

gksu synaptic

run

enter root password, then search for and install "virtualbox"

then virtual box acts as a hardware computer, as in running windows as a program.  you assign ram to the virtual pc, assign how many processors the virtual pc can run.  then mount the windows ISO to a virtual cd drive. and boot the virtual computer....  setup and install windows as if it were going on your actual computer.  install apache on the windows machine to serve the files too and from the host computer through firefox on the host linux machine / internet explorer on windows machine.  i have pictures of this on my master thesis thread....  found here

[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)

linux osx and windows all on the same computer, all at the same time....  towards the bottom of the thread.

---

