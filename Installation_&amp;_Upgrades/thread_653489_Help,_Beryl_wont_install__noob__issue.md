---
title: "Help, Beryl wont install  noob  issue"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by mrchaos101 on 2007-12-30
I am using the code on this site:

[http://onlyubuntu.blogspot.com/2007/03/how-to-install-beryl-with-latest-nvidia.html](http://onlyubuntu.blogspot.com/2007/03/how-to-install-beryl-with-latest-nvidia.html)

The problem I am having is with this part of it:

Adding Source list

you need to edit /etc/apt/sources.list file

sudo vi /etc/apt/sources.list

Add the following line for the latest beryl (Both i386&64 bit)

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

Save file and exit


The command prompt ( i guess we call it a Terminal here?) shows the stuff in this file.
I cant get it to past and save?  No txt editor seems to come up.  The line

sudo vi /etc/apt/sources.list

just seems to print in the Terminal window what the contents are of that file.

I closed window and tried ot open up new Termainal and it seems to be bitching about 2 files or something.


HELP :confused:

---

### Post by taurus on 2007-12-30
If you cannot handle vi/vim, use gedit.

```
gksudo gedit /etc/apt/sources.list
```

p.s.  To get out of vi, press **[COLOR="Blue"]:q![/COLOR]**.

---

### Post by mrchaos101 on 2007-12-30
Great now

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- sudo apt-key add -

dont seem to work

ALso im scared I messed my new system up.

Seen something on another forum that says Beryl is no more? 

Part of what I was doing this was to have my windows burn up in flame.

What do I use and is there a step by step instruction for the install like that web link i posted?

---

### Post by SOULRiDER on 2007-12-30
Beryl is dead. It merged back with compiz.

Look for a guide on how to install compiz fusion (its already installed in Ubuntu 7.10)

---

### Post by mrchaos101 on 2007-12-30
You must remember that to use XGL/Compiz or even the drivers, you must use the kernel that matches your processor. Ex: if you have a P4 HT, you should use kernel 686-smp; if you have a AMD K7, kernel k7... as follow:

What do I use for my AMD 64bit x2 cpu?

---

### Post by taurus on 2007-12-30
Remove the beryl repo that you added to your /etc/apt/sources.list.  Then, have a look at this guide.

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by mrchaos101 on 2007-12-30
> **taurus said:**
> Remove the beryl repo that you added to your /etc/apt/sources.list.  Then, have a look at this guide.

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)



I dont know how to remove it.  Im 100% noob to this.  Im a windows user looking at changing over.

---

### Post by SOULRiDER on 2007-12-30
> **mrchaos101 said:**
> I dont know how to remove it.  Im 100% noob to this.  Im a windows user looking at changing over.

Remove the lines that you added to /etc/apt/sources.list

---

### Post by taurus on 2007-12-30
> **mrchaos101 said:**
> I dont know how to remove it.  Im 100% noob to this.  Im a windows user looking at changing over.

```
gksudo gedit /etc/apt/sources.list
```
And remove 

```
deb http://ubuntu.beryl-project.org feisty main
```
Then, add these two lines to the end of it.

```

deb http://ppa.launchpad.net/amaranth/ubuntu feisty main universe 
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main universe

```
Save it and close the gedit window.  Now, you just have to update your list and install compiz.  

Look at the link that I provided in my previous reply.

---

### Post by mrchaos101 on 2007-12-30
Ok i think I got compiz running

I got wobly windows now, but I cant seem to figure out how to get the windows to burn up in fire when I close them.

---

### Post by SOULRiDER on 2007-12-30
I thinkt he option is in the animations section of the configuration program.

---

