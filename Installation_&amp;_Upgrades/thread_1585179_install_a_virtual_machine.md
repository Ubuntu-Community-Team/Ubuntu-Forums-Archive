---
title: "install a virtual machine"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by turquer on 2010-09-30
New in ubuntu :oops:

Hi all
i am new at Ubuntu 10.04 . i want to install a virtual machine to my ubuntu. 
i ve downloaded an rpm file from the vm web site but i could not install it. So i got crazy and delete the rpm file :D
i need to understand the mentality for how to install something to ubuntu or linux...as a windows user it is being hard for me but i really want to get used to this..
can any of you help me step by step how to install an executable file to linux...lets say how to install a virtual machine program to ubuntu?

thanks alot for the help,
best wishes

---

### Post by SlugSlug on 2010-09-30
instead of RPM (redhat files)  get DEB files -- -- BUT only if you really must

check out software centre first,

---

### Post by Grenage on 2010-09-30
When it comes to installing files in Linux, you'll usually get one of the following:

Source code - You compile it yourself.
Deb/RPM etc - A package that will generally resolve dependencies for you.
Bin/sh - A script which you make executable, then run.

Debs (for Debian-based distos like Ubuntu) are the easiest.

---

### Post by turquer on 2010-09-30
i ve checked the software center and couldnot found a program like vmware virtual machine

can you help me how to get the correct program from internet and install it to ubuntu?

---

### Post by Grenage on 2010-09-30
Virtualbox is available in the package manager, that might be worth a look.

---

### Post by turquer on 2010-09-30
Thanks a lot i will check it

---

### Post by turquer on 2010-09-30
ive found on the sw center and installed virtualbox ose but it does not have the usb support!
simply i need a virtual machine program to install and use :( it getting so boring...

---

### Post by turquer on 2010-09-30
i really need a help

---

### Post by Grenage on 2010-09-30
Have a look here:

[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu)

---

### Post by turquer on 2010-09-30
i've tried the steps that are written in the page but it did not worked!,

sudo apt-get install virtualbox-2.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-2.2: Depends: python2.5 (>= 2.5) but it is not installable
E: Broken packages

---

### Post by Grenage on 2010-09-30
Look in Synaptic Package Manager, search for "Python".  What version(s) are installed?

---

### Post by turquer on 2010-09-30
2.6.5.0-ubuntu1 it says

---

### Post by turquer on 2010-09-30
so what shall i do ?

---

### Post by snowpine on 2010-09-30
Why are you installing Virtualbox 2.2? It is a very old version. 

You can download the latest VirtualBox 3.2 PUEL (with USB support) from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Be sure to install the correct version for your Ubuntu release (Lucid, Karmic, etc.) and architecture (i386 or amd64).

We have an entire subforum here all about virtualization. Be sure to read the "sticky" threads at the top!

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by turquer on 2010-10-01
thanks a lot for the help snowpine and sorry for late answer, quite busy nowadays....
i will try to do so..

---

