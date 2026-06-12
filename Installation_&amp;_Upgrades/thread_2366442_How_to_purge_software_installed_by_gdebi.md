---
title: "How to purge software installed by gdebi?"
date: 2017-07-17
forum: Installation &amp; Upgrades
---

### Post by cleaf on 2017-07-17
I installed a network software, lantern. It doesn't work well on Ubuntu 16.04, so I want to remove it. 

Actually, I don't fully understand what is gdebi. 

When I try "sudo apt-get purge lantern", there are some messages:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms dkms lib32gcc1 libc6-i386 libjansson4 libvdpau1 libxnvctrl0 mesa-vdpau-drivers screen-resolution-extra
  vdpau-driver-all
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  lantern*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 15.7 MB disk space will be freed.
Do you want to continue? [Y/n] 

It is safe to purge the software installed by gdebi using "sudo apt-get purge" or even "sudo apt-get autoremove"? 

Following the messages, I can remove all the related packages. If the "sudo apt-get autoremove" can guarantee all the packages listed are only used in the software to be uninstall?

Thanks a lot.

---

### Post by deadflowr on 2017-07-18
Yep.
You can purge packages you installed with gdebi.
(You can purge any package you installed, regardless of installation method)

As for the autoremove command, all those packages where installed when you installed another package (or packages) and the package you originally installed is no longer installed
(or the package was upgraded to a new version which no longer requires the listed packages)

So there is one main caveat to autoremove and that is that sometimes you might install a package which also needs another package to be installed, then later on you might find that you no longer need or want to have the original package installed anymore, but you may find that one (or more) of the required packages it needed are something(s) you like having, in which case you would not want to run the autoremove command, as then those packages would get removed. If that makes sense.

---

