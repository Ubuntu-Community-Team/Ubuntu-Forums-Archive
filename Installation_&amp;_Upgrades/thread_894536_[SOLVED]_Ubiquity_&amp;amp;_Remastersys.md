---
title: "[SOLVED] Ubiquity &amp;amp; Remastersys"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by Darokgoodnes on 2008-08-19
Somewhere in here,  I've done something idiot-worthy,  but I can't find where.

I'm  trying to install remastersys.  Here are the results of the apt-get:

> 
 sudo apt-get install remastersys
[sudo] password for darok: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  remastersys: Depends: squashfs-tools but it is not installable
               Depends: casper but it is not going to be installed
               Depends: libdebian-installer4 but it is not installable
               Depends: os-prober but it is not installable
               Depends: ubiquity but it is not going to be installed
               Depends: user-setup but it is not installable
               Depends: discover1 but it is not installable
               Depends: syslinux but it is not installable
E: Broken packages
darok@darok-desktop:~$ 


I've tried installing the individual components via synaptics, but can only successfully install a few.  It won't grab the dependencies for ubiquity;  it just refuses to install.  what have I done wrong?

Ubuntu 8.04, btw.

TLDR: How do I install ubiquity,  and how did it not get installed from the livecd?

---

