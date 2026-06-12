---
title: "Where is openssh-server on kubuntu 6.10?"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2006-11-22
I just installed Kubuntu i386 6.10 from the alternate CD. Booted the live Cd and ran the install icon from the desktop. Openssh-client is installed by default, but when I

$ sudo apt-get install openssh-server

it tells me that openssh-server can't be found although it is referenced by other packages. All repositories have been enabled in sources.list. I just want to use ssh with freenx to connect to my box remotely.

---

### Post by bigken on 2006-11-22
try sudo apt-get update  
sudo apt-get upgrade 
the sudo aptitude install openssh-server

---

