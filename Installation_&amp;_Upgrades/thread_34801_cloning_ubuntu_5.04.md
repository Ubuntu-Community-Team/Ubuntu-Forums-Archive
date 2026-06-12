---
title: "cloning ubuntu 5.04"
date: 2005-05-16
forum: Installation &amp; Upgrades
---

### Post by hela on 2005-05-16
I'm want to clone all computers in our school from a tarball of another computer with ubuntu 5.04. 

On first boot of the cloned pc I need hardware detection of several pci hardware. 
[list=1]
[*]Is it done by hotplug?
[*]How can I start a new hardware detection on first boot?
[/list]

---

### Post by nad on 2005-05-16
Hardware detection is performed on every boot automatically by design with the linux kernel.

Unless you are using a custom kernel with removed features, few if any changes will be necessary.

Yes, some of the driver modules are automatically loaded by the hotplug sub-system.

---

### Post by az on 2005-05-16
Hard drive information (fstab) and video card configuration are going to have to be done by hand since you will not be using the installer`s tools...

---

### Post by hela on 2005-05-16
Thanks.

I will try an installation next days.

I have a tool running on damn small linux (live cd) to create a tarball from any running linux system and restore it over nfs.

Additional there is a tool for fast and easy configuration of a server with dhcp-server, name-server, samba-server, nfs-server, proxy-server and nis-server, which is running on Fedora at the moment. If anyone is interested in it, I can post a link in a few days.

---

### Post by hela on 2005-05-16
How can I use the installer tools on first boot?

---

### Post by nad on 2005-05-16
At first boot, enter recovery mode and confirm valid entries in /etc/fstab. I would suggest that the first boot be without a network connection.

You will also have to edit the /etc/hostname file for each machine so that they have different names, and if necessary, give each machine a distinct network address,

Then do a: dpkg-reconfigure xserver-xorg  to configure the graphical display for this machine.

There are probably other details that escape me at the moment. You will not be using ubuntus' installer as it is not designed to be used this way.

---

### Post by hela on 2005-05-17
Thanks.

Partitions are the same (except size) on all computers and each one gets its ip by dhcp. The xserver must be reconfigured.

---

