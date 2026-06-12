---
title: "Package 'mdamd' has no installation candidate"
date: 2015-02-20
forum: Installation &amp; Upgrades
---

### Post by blackknight2 on 2015-02-20
I installed Ubuntu 14.04.01 installation (?) on a new box with a single SSD in a (futile) attempt to recover RAID data from 4 SATA drives in same box, but stuck on this error.
My steps:
  boot Ubuntu from local SSD drive
  launch Terminal
me:
  sudo apt-get install mdadm
Ubuntu:
  Reading package lists... Done
  Building package dependency tree
  Reading state information... Done
  Package mdadm is not available, but is refered to buy another package.
  This may mean that the package is missing, has been obsoleted, or
  is only available from another source
  E: Package 'mdadm' has no installation candidate
Huh?
Much web searching later, I still have no meaningful answer.
Not exactly the experience I was hoping for.
Any constructive advice on how to this stupid software working would be appreciated.

---

### Post by steeldriver on 2015-02-20
Can you please run

```

sudo apt-get update

```

and copy-paste the results here (between CODE tags)?

---

### Post by mc4man on 2015-02-20
> I installed Ubuntu 14.04.01 installation (?)  If you don't know then the  results of the suggested sudo apt-get update command will show clearly.

> Package mdadm is not available, but is refered to buy another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'mdadm' has no installation candidate

If you actually did do an install then that suggested command will have  solved  your install issue. Any new Ubuntu install needs the sources updated *before* one can install packages

---

### Post by blackknight2 on 2015-02-21
My error: installing Ubuntu without a network connection.
The reason I'm attempting this experiment with Ubuntu is to perform a specific task that has nothing to do with the internet; I do not want to connect the machine to the internet.

My simple mind is having a degree of difficulty understanding why I need an inter connection to install a component of Ubuntu from a ISO/DVD that was just downloaded from the internet.
Is this some form of homage to GNU or some sort of inside joke for the *nix crowd?  If so, it's lost on me.
After burning another hour unsuccessfully attempting to download and install Keryx and Python 3.5, oops, no it's got to be 2.6. Oops, not 2.6.x. Ok 2.0.  No that doesn't work either. sigh.
If I sound frustrated, it's because I am.  Where was I?  Oh, yeah, trying to get mdadm to install without an internet connection...  Not without internet access, mind you.  Just not on that box.

It really doesn't seem like this should be this difficult.
Any constructive advice is welcome.

---

### Post by MAFoElffen on 2015-02-21
LOL-- (<--Sorry) 

The full version has limitted space on the disk. I think if you were doing the install from the Server Edititon disk, that it has that package on that install disk. I've done installs of server without any connection. 

I would understand it not being on the full desktop edition disk... Although never knew it was not and assumed it was... The Desktop ISO is not really meant to be full DVD iso, like other distro's, but also not meant to be a full net install either. So a balance of...

But you know you can do a net-less install of a system also right? If you manually download the package deb files needed to a usb drive, you can transport the needed files to the net-less system to install it during the install. During the install, press <cmtrl><shift><F2> to pop out to a shell, manually install any packages or needed drivers from that USB... Type "exit" to get back into the installer, to continue installing. The drawback to that, is you also have to download any needed dependency packages...

---

