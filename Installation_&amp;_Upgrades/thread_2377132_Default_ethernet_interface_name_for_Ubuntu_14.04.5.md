---
title: "Default ethernet interface name for Ubuntu 14.04.5 in Kickstart"
date: 2017-11-09
forum: Installation &amp; Upgrades
---

### Post by dave_f2 on 2017-11-09
Hi, I'm trying to figure out what the default ethernet interface is in Ubuntu 14.04.5 for a Kickstart script I'm building for a VMWare machine. I thought the interface was set to eth0, however when I specify that in Kickstart, I still encounter errors during the automated install process. Can anyone help?

---

### Post by alwayshacked on 2017-11-09
Having had a quick look, Kickstart seems to be a file which helps you create a virtual pc on esxi and possibly other vmware products like maybe workstation.

Create the kickstart file as you want the virtual pc to be, ie with how ever many nics you need, when linux is installed it will detect the virtual nics and install/enumerate the virtual nics accordingly.

In linux to find out what they are called, use 
sudo apt-get install net-tools
and then run 
ifconfig to get a list of the network cards.

You'll see things like
empls0
rl0
lo

Depending on the type of (virtual) hardware linux (or BSD) see's will depend on what the network card gets enumerated to, so realtek nics are rl and then 0 for the 1st, 1 for the 2nd (hungarian notation), so if you have two realtek nics expect to see rl0 and rl1. motherboard nics tend to be seen as empsl0, and finally lo is the local loop nic/adaptor ie 127.0.0.1.

This might also be relevant for you, if you are having difficulty getting the kickstart file setup
[https://communities.vmware.com/thread/511330?start=0](https://communities.vmware.com/thread/511330?start=0)

and this might also be relevant [https://communities.vmware.com/thread/155184](https://communities.vmware.com/thread/155184) because with virtual pc's on vmware products, you can change the order of nics which can then introduce problems with the virtual OS setup, in particular say a virtual pc running as a firewall with many nics for different network segments and/or vlans.

hth

---

### Post by dave_f2 on 2017-11-13
Hi alwayshacked,

Thanks for your reply. To my knowledge Kickstart is just a way to automate Ubuntu installs with predefined settings. I don't have this issue with Ubuntu 16.04, but Ubuntu 14.04 seems to do something different with the NIC card it uses during the install process to connect to the internet. In 14.04, the ethernet nic is 'eth0' by default, but even when I specify this in my Kickstart file, the automation doesn't work at all and breaks at the beginning of the automated install process. Installing net-tools is great, but it doesn't help during the initial install process when you need to specify the network card to use. Without getting that right, everything else will fail to work. I'll try the VMWare method and see if that does anything.

---

