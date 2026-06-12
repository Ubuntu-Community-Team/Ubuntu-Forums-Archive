---
title: "Ubuntu Server: Unable to Install Selected Kernel Package"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by L0neRanger on 2010-03-15
I've been trying to install Ubuntu Server on an old server since a couple of days and have been unsuccessful.

I've google'd a bit but found no solid solution yet to this problem. Everything goes fine and I'm able to partition my SCSI drives and everything. After the installation starts unpacking and copying files this happens.

[IMG]http://harshay.com/doc/install.jpg[/IMG]

I have to mention that I'm installing from a USB drive with the following added at the end of the normal install options:

```
--install cdrom-detect/try-usb=true
```
Version I'm trying to install: Ubuntu 9.10 i386 Server
CPU: AMD Athlon XP 2000+
RAM: DDR 2*256MB
MOBO: ECS K7VTA3 VIA KT266A socket A DDR


If someone has any solution or tips for me, it would be greatly appreciated.

Cheers!

---

### Post by zvacet on 2010-03-15
If you are installing server you don't need linux-generic-pae kernel.Use server kernel.

---

### Post by L0neRanger on 2010-03-15
> **zvacet said:**
> If you are installing server you don't need linux-generic-pae kernel.Use server kernel.
I figured that I might not be needing but how do I not install linux-generic-pae?

I'm using the install cd for Ubuntu-Server - is there an option for me to choose not to install linux-generic-pae?

---

### Post by L0neRanger on 2010-03-16
Installed Ubuntu Server 8.04 LTS without an issue.

Must be some problem with the 9.10.

Issue Solved.

---

### Post by koba101 on 2010-03-16
not really....why would it work for 8.04 amd mot 9.10? are you sue you selected the server edition for 9.10?

---

### Post by L0neRanger on 2010-03-16
> **koba101 said:**
> not really....why would it work for 8.04 amd mot 9.10? are you sue you selected the server edition for 9.10?
yeah that I'm sure of. It WAS a 9.10 server edition install cd.
I just finished the painful process of upgrading from 8.04 to 9.10 - Everythings peachy.

---

### Post by L0neRanger on 2010-03-20
Just updating everyone,

I've downloaded the latest copy Ubuntu Server 9.10 and it installed perfectly.
No problems so far.

---

### Post by Tolaris on 2010-12-11
> **zvacet said:**
> If you are installing server you don't need linux-generic-pae kernel.Use server kernel.

As of Lucid (possibly Karmic), there is no i386 server kernel. The linux-server package is just a metapackage that depends on linux-generic-pae.

---

