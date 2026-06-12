---
title: "libc6-dev broken packages"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by jdimstrnate on 2012-01-15
Im somewhat new to Linux but I am trying.  I have some broken packages that wont go away.
I have tried suggestions from other posts such as:

apt-get -f install
apt-get autoremove
dpkg --purge

----------------------------------------------------------------------------------
apt-get install usbutils
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Breaks: gcc-4.4 (< 4.4.6-4) but 4.4.3-4ubuntu5 is to be installed
             Breaks: pkg-config (< 0.26-1) but 0.22-1build2 is to be installed
E: Broken packages
------------------------------------------------------------------------------------

I am confused about the dpkg --purge command.  what am I supposed to purge?  Is it libc6-dev ?

Any advice would be greatly appreciated.

---

### Post by dino99 on 2012-01-15
I dont know what you are trying to do :(
But each command you run might start with sudo, its very important fot the system security.
All you need for updating/upgrading/installing is to use synaptic (sudo apt-get install synaptic, sudo synaptic; then on the left pane, glance at broken package)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(be patient it can take a while, dont stop it before it end itself)

---

