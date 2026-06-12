---
title: "Can't find linux-source or kernel-source with synaptic or apt-get install"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by Bonefeather on 2008-03-08
I'm trying to update to the latest NVIDIA GeForce 8600 GT drivers on my laptop.  One of the steps involved in this, apparently, is installing a linux-source package.  I just installed Ubuntu today for the first time, so I'm very new at the terminology.  Anyway, when I tried the command "sudo apt-get install linux-source" as directed, I got the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-source

The same thing happens when I try the same command with kernel-source.  Synaptic doesn't find those packages either.  Any ideas?

I was able to use Synaptic to install other packages earlier today, and my Internet connection (obviously) is working fine.  Any help is much appreciated.  Thanks!

---

### Post by mikewhatever on 2008-03-08
Try <sudo apt-get install nvidia-glx-new>. That should install the driver and the dependencies.

---

### Post by Rocket2DMn on 2008-03-08
You have to append the kernel information to it, so when you search, it would look like this:
```
sudo apt-get install linux-source-$(uname -r)
```
since the command "uname -r" returns the kernel version.

You may need to enable the source code repository from System->Administration->Software Sources

---

