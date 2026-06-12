---
title: "Apt-get install from local file system"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by waperboy on 2008-07-18
Hi,

I have a palmtop computer with Ubuntu 8.04 installed onto windows as the 'install in windows' option. There is no internet connection available - the only way to copy files is via usb-stick.

How do I copy packages via the usb-stick, and then install them with apt-get or dpkg?

It's not possible to run dpkg-scanpackages, it does not seem to be installed.

---

### Post by alenis on 2008-07-18
You can, for example, copy the package you want to install on the Desktop and then double-click it. This action will open the package with gdebi, which will perform the installation

---

### Post by gniltaws on 2008-07-18
If it is a .deb: ```
sudo dpkg -i /path/to/file.deb
``` Not sure if that helps.

---

### Post by sisco311 on 2008-07-18
copy the files to the /var/cache/apt/archives directory 
and install the packages with apt-get, aptitude, 
Synaptic Package Manager or Add/Remove ...

---

### Post by waperboy on 2008-07-19
Thanks for the replies guys - will try :)

> **sisco311 said:**
> copy the files to the /var/cache/apt/archives directory 
and install the packages with apt-get, aptitude, 
Synaptic Package Manager or Add/Remove ...

I've tried this already - didn't work, I'm afraid.

---

### Post by Partyboi2 on 2008-07-19
You could try using the [[COLOR=Blue]generate package script[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") in synaptic [[COLOR=Blue][/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")

---

### Post by waperboy on 2008-07-21
The only method that seems to work is the double-click method. A bit tedious to have to follow all dependncies, only to end up with a circular dependency (g++ needs libstdc++ needs g++)...

Any thoughts on how to resolve this?

---

### Post by waperboy on 2008-07-31
Time to bump this up a bit...

---

### Post by mattduckman on 2008-07-31
i have found that if you have all the deb's in one folder, using "sudo dpkg -i *.deb" works pretty well with dependency issues, assuming you have all the necessary packages.

---

### Post by tianyun16 on 2011-01-10
Yes .I have the same problem
If you use dpkg command to install deb file .
like this :sudo dpkg -i  name.deb
so you will see the Dependence problem 
And you fine the depandence file and use dpkg again .
like this: sudo dpkg -i a.deb b.deb c.deb etc.

---

### Post by somekool on 2013-01-12
looks like I found the solution.

install a deb file from the command line and dealing with the dependencies automatically.

sudo gdebi file.deb

tested with steam for linux

---

### Post by sisco311 on 2013-01-12
Old thread closed.


[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

---

