---
title: "reinstalling linux-image-2.6.31-22-generic to upgrade from Ubuntu 9.10"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by klemensmeyer on 2010-11-04
I've searched for the error message I encountered, but couldn't find the string, but apologize if this is redundant. I am trying to upgrade from Ubuntu 9.10. When I run Synaptic Package Manager, I get the message 

"E: The package linux-image-2.6.31-22-generic needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report." After that, Synaptic Package Manager closes.

I have already tried  sudo apt-get update and sudo apt-get install -f, which were successful. Here's what happened when I tried to run sudo aptitude reinstall linux-image-2.6.31-22-generic:
===================

kmeyer@ubuntu:/$ sudo aptitude reinstall linux-image-2.6.31-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  linux-image-2.6.31-22-generic 
The following packages will be REMOVED:
  libdns50{u} linux-headers-2.6.31-15{u} linux-headers-2.6.31-15-generic{u} 
  linux-headers-2.6.31-16{u} linux-headers-2.6.31-16-generic{u} 
0 packages upgraded, 0 newly installed, 1 reinstalled, 5 to remove and 1323 not upgraded.
Need to get 0B of archives. After unpacking 164MB will be freed.
Do you want to continue? [Y/n/?] Y
E: I wasn't able to locate file for the linux-image-2.6.31-22-generic package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the linux-image-2.6.31-22-generic package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

=====================

How do I go about doing the manual fix?

---

### Post by mörgæs on 2010-11-07
You could try 

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

but I would rather do a clean install of 10.04 or 10.10.

---

