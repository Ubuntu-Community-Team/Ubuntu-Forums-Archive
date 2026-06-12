---
title: "Can't upgrade anything"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by erafael on 2011-11-15
Whenever I try to upgrade, I receive the following error:

dpkg: warning: files list file for package `protobuf-compiler' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ptouch-driver' missing, assuming package has no files currently installed.
dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `foomatic-db-compressed-ppds': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

I have tried:
sudo dkpg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

Nothing worked so far.

Any ideas?

---

### Post by 2F4U on 2011-11-15
Seems as if something is corrupted. Can you try to reinstall the packages that get the files list file warning, for example

sudo apt-get install --reinstall protobuf-compiler

---

### Post by Frogs Hair on 2011-11-15
Hello and Welcome  

Start with some information about your computer . When searching ptouch-driver as noted in your error output it comes up as a Brother driver .

---

### Post by gordintoronto on 2011-11-15
If you run Disk Utility (you might need to install it) and point to your hard drive, does it say "disk is healthy"?

---

### Post by erafael on 2011-11-15
I have tried what you suggested.
Reinstalling command did not work. Hard Drive (SSD) appears to be healthy as well.
 
I am on a custom made machine with Ubuntu 11.10 on it.
 
The printer I use is EPSON EP-802A. I do not have any other non-standard devices connected to it except the above printer, standard keyboard and mouse.

---

### Post by erafael on 2011-11-17
I have tried different things and nothing worked, so finally reinstalled the OS

---

