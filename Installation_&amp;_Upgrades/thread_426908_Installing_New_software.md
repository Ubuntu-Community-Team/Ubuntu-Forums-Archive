---
title: "Installing New software"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by shahin on 2007-04-28
I am trying to install wireshark, but upon selecting the package in Synaptic, I get an error message saying:
Cannot install 'wireshark'

This application conflicts with other installed software. To install 'wireshark' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.

---

### Post by taurus on 2007-04-28
Run it from a terminal to see which package conflicts with it.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install wireshark
```

---

### Post by shahin on 2007-04-29
Thanks for the reply.  Here is what I get:
sansari@karoon:~$ sudo aptitude install wireshark
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  wireshark wireshark-common 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 7816kB of archives. After unpacking 31.7MB will be used.
The following packages have unmet dependencies:
  wireshark: Depends: libadns1 which is a virtual package.
             Depends: libpcre3 (>= 4.5) which is a virtual package.
  wireshark-common: Depends: libadns1 which is a virtual package.
                    Depends: libpcre3 (>= 4.5) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

---

### Post by shahin on 2007-04-29
Could it be I have installed the wrong version of Ubuntu?  I wanted to install the server.  But regardless of that I should be able to ssh into a machine.  Not sure what is going on.  Please help.

---

