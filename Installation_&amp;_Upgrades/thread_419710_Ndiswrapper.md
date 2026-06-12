---
title: "Ndiswrapper"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Philistine on 2007-04-23
I can't install Ndiswrapper.

It keeps asking to connect to the net - the whole reason I am trying to install it is because I can't use my wireless card!

I did it with the beta, but did a fresh install with the released 7.04.

- I have the cd in the drive
- I have tried searching add / remove programs and the synaptic package manager.  Both aren't working.

I am starting to think I should just uninstall it and live with XP.

Help.

---

### Post by Philistine on 2007-04-23
ok

found the deb files

why couldn't they just put these onto the CD???

sigh

---

### Post by seeklinux on 2007-04-23
If you look at my post [here]("http://ubuntuforums.org/showthread.php?t=187659&page=6") (look for post by seeklinux) it seems (at least in the past) that ndiswrapper is not supplied on the Live CD. If still true with 7.04, this makes connecting to wireless difficult if you need to get to the network first to install ndiswrapper to get to the network.

For Feisty Fawn (7.04) I think you need to get [this one]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb") instead of the one I referenced in that previous post (for Edgy). Also it appears you need the [common file]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb") too if you don't have that installed already. Hopefully you have access to a USB drive or something like that on which to copy these files to so you can get them onto your Ubuntu machine.

Once on the machine,  the commands to install packages is:

sudo dpkg -i ndiswrapper-common_1.38-1ubuntu1_all.deb
sudo dpkg -i ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb

If you have an AMD instead of Intel processor there is an AMD version of the ndiswrapper-utils package you should get instead.

Hope that helps.

---

