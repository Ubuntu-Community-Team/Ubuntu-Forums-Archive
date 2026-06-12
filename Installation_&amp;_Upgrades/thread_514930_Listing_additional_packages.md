---
title: "Listing additional packages"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by frisket on 2007-08-01
I want to upgrade from Edgy to Feisty, but I want a list of all the extra packages **I** have installed, so that I'll know what to add once I get Feisty installed.

**NOT** repeat **NOT** a list of all packages, not a list of the packages that were originally auto-installed, and not a list of updates, but a list of all the packages that I personally have asked for by clicking on them manually in Synaptic or Add/Remove.

There's a History button in Synaptic, but it only produces a GUI-able list and I want something I can print off or edit.

---

### Post by bulldog060 on 2007-08-01
if you are trying to make a "jumpstart" type kit to set yourself up on the new system here is what I did

on the current system:

**$ ls /var/lib/dpkg/info |grep \.list$ |cut -d \. -f1 > ~/package_list**

( for non command line people, this lists the contents of the package info directory but each package has several files so I picked the ones ending in .list and then strip the extention to write the clean list into a file called package_list in my home directory *i don't do /var/lib/dpkg/info/*.list because that will give me the path as well* )

after taking a look at the list and removing things i didn't want i copied this file over to my new system and did this:

[B]$ for pkg in `cat package_list`; do
> apt-get -y install $pkg
> done [/B]

( apt-get -y install forces yes for everything so you can leave it alone, and when you do the install if it already has the package it will ignore it so you only have to remove the packages you know you don't want/need on the new system from that list )

also make sure you update (or copy) your /etc/apt/sources.list first or you might not find some of the packages.

hope this helps

~ron

---

### Post by Pumalite on 2007-08-01
Or you can try AptON: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by frisket on 2007-08-13
> **bulldog060 said:**
> after taking a look at the list and removing things i didn't want

But that's the problem: I want a list that only shows the packages I have installed additionally *after* installing the default Edgy from CD.

Is there really no way to get a list of packages with the date they were installed on?

---

### Post by zvacet on 2007-08-13
Try in** synaptic>files>history**

---

### Post by frisket on 2007-10-15
> **zvacet said:**
> Try in** synaptic>files>history**

But that's in GUI mode. How do I get this data as a text file listing?

---

