---
title: "Install Packages from cdrom?"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by Randymanme on 2012-10-25
Hello, 

I'm presently without an internet connection -- I'm at the public library right now.

It's my understanding that packages can be installed to Ubuntu from CD/DVD without having to have an internet connection.  But there must be something I'm missing here.  Synaptic package manager>respositories (for those Ubuntu releases or Ubuntu-derivatives the have synaptic package manager) has a place to select installation from CDROM: just put in the disc.  But I haven't had it work for me at all -- not on Ubuntu, Ultimate Edition, Pinguy, or Mint.  As it is, I have Ubuntu, Ultimate Edition, Pinguy installed so that I can use all the packages I want without having to have an internet connection to download and install them all on any one install.

12.10 :confused: by the way is especially unusable; no synaptic, no gdebi, no gparted, no screensaver . . ..  Is there someway I can just download an update for a fresh install?  So far, I haven't the dependencies on any of my installed OSes the install APtonCD.  Is this what the Alternate Install CD is for?

Having wait in line for an hour slot on a public computer is severely limiting my googling opportunities so it's more efficacious to just ask.

Any help would be much appreciated.  Thanks.

---

### Post by newb85 on 2012-10-25
I'm guessing you're not in the library anymore, but I'll answer anyways.

You have to enable the CD/DVD source before it can be used.

In the Ubuntu Software tab of Software Sources (in Software Center, Edit>Software Sources), at the bottom, make sure your removable media is checked.  Once that's done and the CD/DVD is in place, you may have to run
```
sudo apt-get update
```
for the software to show up in the Software Center.

---

