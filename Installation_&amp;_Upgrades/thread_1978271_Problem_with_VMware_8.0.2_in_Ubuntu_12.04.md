---
title: "Problem with VMware 8.0.2 in Ubuntu 12.04"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by siledrolf on 2012-05-11
[SIZE=2]Hi everyone!!

I have a big problem and I am right now kind of frustrate. Recently I installed VMware 8.0.0, uninstalled it and then install VMware 8.0.2 in my ubuntu 12.04, and I notice that I cant run any version of VMware in this version of ubuntu. I tried to fix the VMware 8.0.2 erasing and running this commands recommended in a forum:

sudo etc/init.d/vmware stop
sudo lsmod | grep vm*
sudo rmmod vmmon.o
sudo rmmod vmci.o
sudo rmmod vmblock.o
sudo rmmod vmppuser.o

sudo rm /etc/rc2.d/*vmware*
sudo rm /etc/rc3.d/*vmware*
sudo rm /etc/rc5.d/*vmware*
sudo rm /etc/rc6.d/*vmware*
sudo rm /etc/rc5.d/*vmware*

sudo rm /usr/bin/vm*
sudo rm -fr /etc/vmware
sudo rm -fr /etc/vmware-vix
sudo rm -fr /usr/lib/vmware-vix
sudo rm -fr /var/run/vmware
sudo rm -fr /var/log/vmware-installer

and I erase the /usr/lib/vmware and /usr/lib/vmware-installer

What can I do?

[/SIZE]

---

