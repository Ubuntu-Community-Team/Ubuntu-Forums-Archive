---
title: "Virtualbox install issues"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by trash19d on 2008-09-23
Hello,

I am having an issue with the installation and running of Virtualbox on Ubuntu 8.0. I have installed it via add/remove and it seems to work through the setup faze, but when I run it to install the OS (windows 2000) i get this error message...

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

I've tried to install the file from the synaptic package manager but I am unsure what the kernel is so I installed them one by one to see if the issue would resolve itself, but it has not. Does anyone know how to fix this?

---

### Post by worx101 on 2008-09-23
Remove that version of virtual box and download the one from sun's website.

It installs and works like a charm.

Just reboot after install :)

---

### Post by trash19d on 2008-09-23
Thank you. Just like you said...downloaded from the Sun site and it works like a charm.

---

### Post by Peter123 on 2008-09-23
I'm in the same boat, but I get the same problem with versions from the Sun site.  I've been searching through posts for several days and can't recall what fixes I've tried (although I do remember issuing a command to do something with the modules for my version of kernel - but can't remember what and don't know if/how to undo it).

I would really like to get Virtualbox up and running and would appreciate any help on this.  Yes I'm a newbie, so please be gentle with me.

---

### Post by Peter123 on 2008-10-16
OK, disregard the last post.  This is a kernel issue with the OSE version.  I got everything from OSE uninstalled and reinstalled from Sun website.  All worked fine.  Kernel issue seems to be common with Virtualbox.  Otherwise it worked like a charm.  By the way, don't forget to install Guest Additions from within Virtualbox - what a difference it makes!

---

