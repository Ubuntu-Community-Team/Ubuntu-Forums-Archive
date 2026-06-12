---
title: "Installing s/w from source, no compiler?"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by Kronocide on 2005-12-05
Hi,

Coming to Ubuntu straight from Slackware. I can't seem to find the compilation tools (autoconf, make, gcc, standard libs), although in the Ubuntu manual forum it says that standard development tools should work out-of-the-box (I think). I just want the standard stuff. All help appreciated!

---

### Post by adwait on 2005-12-05
Hmm...I think you can just install whatever you want with apt get.
```
sudo apt-get install make
sudo apt-get install gcc
sudo apt-get install autoconf
```

---

### Post by 23meg on 2005-12-05
Better yet, ```
sudo apt-get install build-essential
```

---

### Post by DRF on 2005-12-05
The package you probably want to install is build-essential which you can install though synaptic/apt. (It's online in the respositories and wouldn't surprise me if it's on the install CD as well, but can't be sure)

The packages page explaining build-essential is at:
[http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential)

You will still need to get what ever development librarys and source code that the program your compiling needs. But this should hopefully give you C/C++ compilers and make.

Daniel

(If not used to apt-get/synaptic you can open a terminal window and type:
sudo apt-get update
sudo apt-get install build-essential
to get the packages. Alternativly graphically by searching in synaptic in the 'System -> Administration' menu)

---

### Post by adwait on 2005-12-05
aah.......build-essential......I kept trying to remember that name, but couldn't :p

---

### Post by Kronocide on 2005-12-05
Thanks, that's the kind of answer I was hoping for. :-) No network on this box so I will put the package on a CD.

---

