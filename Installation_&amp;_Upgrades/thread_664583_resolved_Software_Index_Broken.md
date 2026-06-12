---
title: "resolved: Software Index Broken"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by JaggedOne on 2008-01-11
I recently tried to update my system and it gave me this error: 
> 
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


I ran that line in the terminal and it gave me this error 

> 
Reading database ... 114536 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr155-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr155-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package avant-window-navigator
Unpacking python-libawn-bzr (from .../python-libawn-bzr_0.2.0-bzr155-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr155-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.5/site-packages/awn/awn.so', which is also in package avant-window-navigator
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr155-1_i386.deb
 /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr155-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


help!

Edit: hey i figured it out myself. Went into synaptic and removed a broken package. That was easier then i thought it would be.

---

### Post by umuro on 2008-01-11
If you know what you are doing and if you really need the problematic package then there is a way to install packages that share a file by mistake. A file should only belong to a single package but such errors happen during updates unfortunately.

Try this. If you do an 

```
sudo apt-get install
```

you get the list of problem packages. Apply the process below for each. I will call the package in question the_package!

```
cd /var/cache/apt/archieves
ls

```
If your *.deb file is not there redownload it
```

sudo aptitude download the_package

```
The FORCE an installation
```
sudo dpkg -i --force-all the_package*.deb

```
-------------------

For any package, you can use "dpkg -i --force-all" when ever you meet an "dpkg error processing .... (Broken pipe)". The package will install. And the complaints will be silenced. And you will be ok if the new package is working!

---

