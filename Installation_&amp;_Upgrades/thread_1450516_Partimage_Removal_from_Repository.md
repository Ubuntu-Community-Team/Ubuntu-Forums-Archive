---
title: "Partimage Removal from Repository"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by indytim on 2010-04-09
I've noticed with some recent Gnome builds, that partimage is no longer available via the repositories.  Anyone know the rationale behind this move?

IndyTim / DataMan

---

### Post by fleder on 2010-05-01
As of Ubuntu 10.04 Server amd64 "sudo aptitude install partimage" is unable to find partimage in the repositories. I would like to access a partimage backup. Does anybody know where to get it?

---

### Post by louieb on 2010-05-01
Just looked in Synaptic - its in the universe (community maintained) repository.  

Running 10.04 32-bit desktop here.

---

### Post by indytim on 2010-05-02
The only thing that I see is the Partimage-docs.  Not the app.

IndyTim / DataMan

---

### Post by BryanFRitt on 2010-05-15
> **louieb said:**
> Just looked in Synaptic - its in the universe (community maintained) repository.  

Running 10.04 32-bit desktop here.

I think partimage has been removed from the **64 bit** repositories, but not the **32 bit** repositories.

To compile from a live CD/DVD do something like this:

[FONT="Courier New"]sudo apt-get install gcc
sudo apt-get install libbz2-dev
sudo apt-get install libnewt-dev
sudo apt-get install libssl-dev[/FONT]

[http://www.partimage.org/Download](http://www.partimage.org/Download)

tar xfjp partimage-0.6.8.tar.bz2

./configure
make
sudo make install

-

I also did a 
sudo apt-get install auto-apt
sudo aptitude install checkinstall
but I don't know if they did anything, or not
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by Mark Phelps on 2010-05-15
Be aware that partimage does NOT work with Ext4 filesystems -- the default for installing Ubuntu 10.04.

---

