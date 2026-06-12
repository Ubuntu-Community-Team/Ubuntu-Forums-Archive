---
title: "VMWare"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by grandsoul on 2007-11-25
Hello folks, I'm having trouble with Ventrilo, i got it working under wine, but it doesn't seem to recognize anything for input via my mic (running a dell d620).  Anyway, figured i'd run the sucker on VMWare via virtual XP.  However, I"m very new to linux, and I have no idea how to install VMWare on the current distro of Ubuntu.  I've searched and searched, but it's all for earlier editions and frankly requires skills I do not yet have.  Can anyone help me?

I'm just looking for a straight forward easy install...which it doesn't look like I'm able to find.

---

### Post by Scunizi on 2007-11-25
Well.. looks like ventrilo is developing a client version for linux. They do have the server version though.. 

To run/install VMware it's better to go to the vmware site and download "server".  Before installing you need to install some stuff. Get to a terminal and sudo apt-get install build-essential.  This will install the needed compilers etc that vmware uses to install itself.  After that it's pretty straight forward.  However I think what you'll find is you'll be able to get the sound working (usually but not always) but may have problems with the mic.. I've never looked for the switch to turn the mic on in a winxx VM.

---

### Post by grandsoul on 2007-11-25
See i've done the essential part, but it's getting the damn vmware to intsall I don't know how.  That part i'm lost....any suggestions on how to get it rolling?  Mind you i come for a windows enviroment, so i'm just used to straight forward click and go...i'm not used to using terminal to get installs going.

---

### Post by grandsoul on 2007-11-26
So no one can help me?

---

