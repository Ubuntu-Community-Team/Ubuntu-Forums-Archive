---
title: "VirtualBox USB Fix ?"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Bobhuber on 2010-04-24
I've been trying with no success to get VirtualBox to recognize my USB printer in Lucid as have many other people according to recent posts. After the latest package update I got an error related to the VirtualBox kernel while trying to start the program with the following
suggestion which worked.
 Type the following from a terminal prompt > sudo  /etc/init.d/vboxdrv setup

This will remove, recompile and reinstall the VirtualBox kernel module.
My USB printer now works in VirtualBox.

---

### Post by wilee-nilee on 2010-04-24
> **Bobhuber said:**
> I've been trying with no success to get VirtualBox to recognize my USB printer in Lucid as have many other people according to recent posts. After the latest package update I got an error related to the VirtualBox kernel while trying to start the program with the following
suggestion which worked.
 Type the following from a terminal prompt > sudo  /etc/init.d/vboxdrv setup

This will remove, recompile and reinstall the VirtualBox kernel module.
My USB printer now works in VirtualBox.

It would be helpful if you confirmed the guest and host OS and in which one you ran this command.

---

### Post by jflaker on 2010-04-24
VirtualBox-OSE (Open Source Edition) is a bit crippled...ie, the USB doesn't work...

Here are some instructions...adjust for your version and use Synaptic to install as this writing is a bit old
[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu]("http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu")

---

### Post by Bobhuber on 2010-04-24
> **jflaker said:**
> VirtualBox-OSE (Open Source Edition) is a bit crippled...ie, the USB doesn't work...

Here are some instructions...adjust for your version and use Synaptic to install as this writing is a bit old
[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu)
These instructions are NOT FOR LUCID. They will prevent you from booting.

---

### Post by wilee-nilee on 2010-04-24
> **Bobhuber said:**
> These instructions are NOT FOR LUCID. They will prevent you from booting.

You are so correct.

---

### Post by Detonate on 2010-04-24
Go here to obtain and install the full featured Virtualbox.  They don't list for Lucid yet but I installed the Karmic version and it is working perfectly.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by dcstar on 2010-04-24
> **Bobhuber said:**
> 
..........
My USB printer now works in VirtualBox.

And so this thread is actually SOLVED, is it?

---

### Post by Bobhuber on 2010-04-24
> **dcstar said:**
> And so this thread is actually SOLVED, is it?
 With the problems I've had with Lucid (I speak for myself only) I can say that on my machine with the package downloaded from the internet it solved the problem  . 
AMD 64 X2 - Nvidia - 3/gig -64bit Lucid (Fresh Install) - VirtualBox 3.1.6 r59338

---

