---
title: "Black screen and login required after update"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by MicroMina on 2011-03-13
Hello all..
Yesterday I found that ubuntu needs to be updated, so I did update and all files were downloaded but I had an error that not all packages could be installed..
I figured I would restart and then try to install the rest of the packages, but now I have a black screen that says:

Ubuntu 10.10 Dell-Inspiron-1564 tty1
Login:
Password:

I tried my ubuntu username and password but I get "Login incorrect"
I tried repair from the recovery menu but that didn't work..

I can see older versions of ubuntu in the boot screen and ubuntu 10.10-25 opens fine but I cant check for updates.. I get "Check your connection", although firefox works normally.
What can I do to fix this?

Thanks.

---

### Post by tommcd on 2011-03-15
> **MicroMina said:**
> 
I had an error that not all packages could be installed..
I tried repair from the recovery menu but that didn't work..
Boot to recovery mode and drop to the command line terminal. 
If you have any 3rd party repositories in your */etc/apt/sources.list* (this includes those all too often problematic PPA repos), then comment them out 
(i.e., put a **#** in front of them. Also comment out any third party repos that may be lurking in files in your */etc/apt/sources.list.d/* directory.
Then try running this:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot
```
If that does not fix it, then try from recovery mode:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot
```
If that does not help then try from recovery mode:
```
sudo dpkg --clear-avail && sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot
```
> **MicroMina said:**
> 
I can see older versions of ubuntu in the boot screen and ubuntu 10.10-25 opens fine but I cant check for updates.. I get "Check your connection", although firefox works normally.

Also try loading a different mirror if you can from: system > administration > software sources, or the software sources in Synaptic Package Manager.

And welcome to the Ubuntu forums!

---

### Post by MicroMina on 2011-03-18
Well, that's weird..
The problem somehow fixed itself!

Thanks tommcd for your help

---

