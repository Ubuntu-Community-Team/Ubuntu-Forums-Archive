---
title: "Not enough space on partition mounted at /"
date: 2017-02-04
forum: Installation &amp; Upgrades
---

### Post by itanon on 2017-02-04
I'm on Ubuntu 12.04 live usb installation and I'm tryin to install Nvidia cuda toolkit, so I've downloaded the .Run file, make it executable then issued the .Run command.
Scrolled the EULA contract, set the directory for installation and confirmed....
The installation seems to starts but the it stops giving me the message:

"Not enough space on partition mounted at /.
 Need 2308316160 bytes
 
 Not enough space on partition mount at /tmp.
 Need 2114567168 bytes.
 
 Disk space check has failed. Installation cannot       c. continue"

On other configuration I've resolved this problem, issuing the command : "mount -o bind /var/tmp /tmp"
Now this doesn't work so I'm stucked.
Anyone know how to solve it?

---

### Post by TheFu on 2017-02-05
12.04 support will end in about 2 months. Beware.
Last time I checked a live USB boot put the OS in read-only mode. Something special (which I don't know what) needs to happen to allow writing to the flash drive.
2,308,316,160

Looks like you need to make / have 2.3GB of available storage that can be written and /tmp/ have 2.1G of available storage that can be written.  This assumes there isn't a bug in their installation script.  So, that would be how to fix the install issue.  Make more storage available that can be written to both those locations.

---

### Post by itanon on 2017-02-06
> **TheFu said:**
> 
Looks like you need to make / have 2.3GB of available storage that can be written and /tmp/ have 2.1G of available storage that can be written.  This assumes there isn't a bug in their installation script.  So, that would be how to fix the install issue.  Make more storage available that can be written to both those locations.
Do you know how to do it (I'm not an expert)?
I've used an 8 GB drive for this installation.

---

### Post by TheFu on 2017-02-06
> **itanon said:**
> Do you know how to do it (I'm not an expert)?
I've used an 8 GB drive for this installation.

Sorry. No.  I haven't tried to run from any flash storage that allowed writes, ever.  

I boot from flash about 5 times a year, but just to install onto normal spinning or ssd storage, never flash storage.

 Look for a way to install onto a flash drive from a flash drive. [https://askubuntu.com/questions/170454/can-i-install-ubuntu-to-my-32-gb-usb-pen-drive](https://askubuntu.com/questions/170454/can-i-install-ubuntu-to-my-32-gb-usb-pen-drive) seems related. Just realize that doing this will drastically shorten the life of the flash hardware. Lots of articles written about that on the web. The shorter life may not matter to you. 

Sorry, I'm not any more help.

---

