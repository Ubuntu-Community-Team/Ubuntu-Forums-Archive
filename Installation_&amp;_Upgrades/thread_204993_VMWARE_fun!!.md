---
title: "VMWARE fun?!?!"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by lUigi_sa69 on 2006-06-27
Got the ubuntu iso, got to admit, never played/used vmware before! tried to get it going by pointing cd to the iso, but when i "boot up", it comes back with error message of no bootable media etc.

Please help!

---

### Post by AndyCooll on 2006-06-27
For VMware it's not the ISO you want (which is a copy of CD/DVD disk), it's a VMware "image". A VMware image is basically a virtual image of a drive with the OS installed.

You can get one from here: [VMTN virtual appliances]("http://www.vmware.com/vmtn/appliances/directory/community.html")

:cool:

---

### Post by lUigi_sa69 on 2006-06-27
Please excuse the "mindless questions....", but from what i understand, its easier to d/load the VM image than try install Ubuntu for myself on VMWare?

---

### Post by FredB on 2006-06-28
Not easier, but more quick. You can use an ISO of Ubuntu and install it in a VMWare virtual machine without problem.

And which VMWare are you using ? If it is VMWare player, you have to use a vmware image. If it is a trial version VMWare or VMWare Server, you can use the ISO from ubuntu.

---

### Post by sharperguy on 2006-06-30
vmware-player will let u install from iso

you just need a blank vm computer to install it ton then edit the file to point it to the iso rather than disk drive

---

### Post by rcarring on 2006-06-30
Go to [http://www.easyvmx.com](http://www.easyvmx.com)

You can create the required vmx config file and hard files there, download them and install Ubunut into the vm. One note, make sure to add a floppy disk drive device even if you don't have a real one on your computer as otherwise the Alternate installer won't pick up the network card.

I have installed Ubuntu several times into vmware and this is a required device to get around the need to install vmware-tools (and for that you need to install gcc anyway).

---

### Post by sharperguy on 2006-07-03
!!!!!!!!!!!!

I think that has been my problem!!!!

*runs off to try it...*

edit: oops, didnt need to run i was already there :P

---

