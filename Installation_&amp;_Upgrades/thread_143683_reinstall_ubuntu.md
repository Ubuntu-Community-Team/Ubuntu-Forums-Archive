---
title: "reinstall ubuntu"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by chrisedu on 2006-03-12
Hello all

I am a new linux user and I was using ubuntu 5.10 for a while on my laptop. 
It seems that I messed up some permissions and system files.
From my user account I can't use sudo commands and it seems that synaptic won't work anymore.

would like to know if its possible to reinstall or restore the system to the default initial state without resinstall the entire system from scratch, since I need to do it from network because I don't have CDROM on this machine.

thx for any help

chrisedu

---

### Post by mlind on 2006-03-13
can you post more verbose details about

*what happens if you try to use sudo commands?
*does your user have adminstration privileges, see System > Adminstration > Users and Groups > Properties > User privileges
*have you changed file permissions outside of your local folder? (/home/$USER)

to play safe, you should to backup your /home folder now and re-install ubuntu.
I don't know if there's script for restoring default file permissions without reinstalling
all packages.

it's possible to install from different media, like from another parition, but I've never done this myself.

---

