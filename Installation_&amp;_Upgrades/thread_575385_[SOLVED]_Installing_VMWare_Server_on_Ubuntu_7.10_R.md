---
title: "[SOLVED] Installing VMWare Server on Ubuntu 7.10 RC"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by ldesilva on 2007-10-14
Hi,

Has anyone tried installing VMWare Server or Workstation on Gutsy? If yes, can you please advise what do I need to do? Some instructions will help lots.

Thanks.

---

### Post by FredB on 2007-10-14
I've done it. Simple.

In synaptic, install linux-headers and build essential.

Then, unpack the tar.gz version of vmware server, and install it in a console.

It will work flawlessly until it asks you for a serial number.

The only bad point is that USB seems not to work ?!

If you can, wait for an official version from ubuntu repositories.

---

### Post by ldesilva on 2007-10-14
When you said, linux-headers and build essentials, can you please elaborate? I am new to linux/ubuntu. 

Thank you.

Found this article, [http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/)
Installing VMWare server now. Thanks.

---

### Post by Thomas Pips on 2007-10-15
Same goes for me, no USB support, nor FTDI USB to serial support :(

---

### Post by ldesilva on 2007-10-15
> **Thomas Pips said:**
> Same goes for me, no USB support, nor FTDI USB to serial support :(
Decided to use VirtualBox, vm on USB external HDD, no problems. :)
Can't get VMWare server to work when I have my VM on my external USB drives. not starting at all :(

---

### Post by FredB on 2007-10-16
> **Thomas Pips said:**
> Same goes for me, no USB support, nor FTDI USB to serial support :(
I am only using vmware server for 64bits linux distros.

Besides this, Virtual box is ok ;)

---

### Post by ldesilva on 2007-10-17
found an article with regards to storing vm's on an external usb drive formatted with ntfs. it is a know problem.

---

