---
title: "Network Installation Ubuntu 10.04"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by arunkumargoge on 2013-01-09
My question
1.Is it possible to network installation of ubuntu ?
2.If it is possible pleas tell me hw

---

### Post by ajgreeny on 2013-01-09
> **arunkumargoge said:**
> My question
1.Is it possible to network installation of ubuntu ?
2.If it is possible pleas tell me hw
What exactly are you trying to do that you are having problems with?  We need much more information to able to help you.

Hardware?
Network requirements?
Wireless or cable?

---

### Post by Cheesemill on 2013-01-09
There are a couple of different methods depending on exactly what you mean by 'network installation'.

The easiest is to boot from a CD made from the mini.iso file. This is a very small CD (around 30MB) that only contains the text mode installer, all of the packages required during or after installation are downloaded directly from the internet. This means that your system will be fully updated from the moment you install it, no need to spend time updating your new system when you first boot it up. The disadvantages of this method are that you still have to boot from a CD and your network needs an internet connection, this could be a problem if the quality, speed or price of this connection are an issue.

The other method is much more involved to set up, but gives you far more flexibility.
This involves installing and configuring a DHCP server, a TFTP server and possibly an NFS server on your network (these can all be on the same machine). The basics of the process are that your DHCP server hands out extra information to your machine regarding the location of the TFTP server, this is then used to download and run the installation files if the client machine is set to boot from the network. These files can be as simple as providing the netboot files from the mini .iso, or if you have an NFS server as well you can set up menus allowing you to boot from a selection of different live CD's, such as Ubuntu CD's, system rescue CD's, Clonezilla etc

There are plenty of in-depth guides around for setting up this sort of thing, Googling for 'ubuntu pxe' should find you what you need.

---

