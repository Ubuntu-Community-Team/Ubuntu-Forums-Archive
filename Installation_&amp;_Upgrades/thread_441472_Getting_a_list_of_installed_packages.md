---
title: "Getting a list of installed packages"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by jbm222 on 2007-05-12
I'm doing a clean install of 7.04 because I'm currently dual booting on a laptop but never use windows, so i'd like to free up the 12 GB its using and move my data to an ext3 partition (it was on FAT32 to share between OS's).   But anyway to the point of my post...

How to I get a list of ALL the packages I have currently installed?  I would like to use this a basis for writing an apt-get command to re-install everything I use after i wipe the drive.

Also, I have another desktop also running ubuntu.  Can I use apt-get to download these packages onto that computer (but not install them), write them to a disk (CD/DVD), and then install them on my laptop?

---

### Post by Tine on 2007-05-12
Open synaptic package manager
then on the panel left click "installed"
then click on the right panel click "installed version" so it will order those packages properly, 
Then select all the installed packages
Then go to: File->Save markings as, tick box to "save full state..."
then enter like packages.txt and hit save
now you can open that packages.txt and open it. It displays install after every package, but you can remove it with replace option in gedit.
With a little editing you can make those on one line.

Using apt-get with switch -d should download packages, but not install.
I think that is what you are looking for.
Definition for the -d switch is:
-d  Download only - do NOT install or unpack archives

-Tine

---

### Post by cryogen on 2007-05-12
> **jbm222 said:**
> How to I get a list of ALL the packages I have currently installed?  I would like to use this a basis for writing an apt-get command to re-install everything I use after i wipe the drive.

Try:

```
dpkg --list
```

--cryogen

---

### Post by nebulus-design on 2007-10-03
Cryogen,

Can the output from " dpkg --list " be used as input to another app on a different computer to match the installed packages?

This is what I'd like to do, for a cluster of computers, get one running, then share the package list across the cluster so all the machine have the same packages and will all upgrade in the same way...

thanks!

---

### Post by zvacet on 2007-10-03
[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html]("http://www.ubuntugeek.com/clone-your-ubuntu-installation.html")

---

