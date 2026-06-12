---
title: "Ubuntu Server 8.04 - fails to install kernel"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by xenomorph99 on 2008-05-04
Hi,

I've been trying to install Ubuntu 8.04 server onto a 2GB compact flash (IDE converter) and having some problems.

I burned the image onto CD then ran a defect check and everything was fine.

I then tried to install 8.04 but I got a message saying something along the lines of "Cannot find/install suitable kernel in APT sources."

Within the installer, I then tried to point it to some ISO images on my HDD but came up with some 'incorrect version' messages. I also tried to revert to using a network mirror - it complained with the same error messages.

I then rebooted and rechecked the CD I was installing from - no problems.

I retried the entire process and got the same message about there not being a kernel available in the APT sources (or similar)

Now, I know 8.04 will install on my hardware because I'm already running it (installed from the alternative install CD) and I'm pretty sure there are no errors either with the CD or the CF (as I've formatted it without problems.)

When I'm installing the server, I've partitioned as follows:

CF
1 partition, ext2, mount point 'root'
SATA drive
multiple partitions but
partition 1 - Windows
.
.
partition 5 - /var, ext3 (50MB)
partition 6 - /tmp, ext3 (50MB)
.
.
remaining partitions are for existing 8.04 install.

i.e. I'm trying to install root, home etc on the CF but to use a couple of partitions on my HDD for /var and /tmp so I don't wear the flash out. I don't really intend to use the /home directory (and this is just an experiment to see how the system responds when using CF for the root filesystem)

Any suggestions, please?

X

---

### Post by Pumalite on 2008-05-04
This might help:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
I wish luck in your HDD scheme.

---

### Post by xenomorph99 on 2008-05-04
Hi,

Thanks for the quick response. I'm not sure how those guides will help me, though, as they appear to be intended for USB installs.

I have a compact flash mounted in an IDE to CF converter - this means that the CF is seen as an IDE hard drive so, supposedly, I shouldn't really need to do anything special in order to install Ubuntu except to try to minimise wearing the flash out which I believe I have done by using /var and /tmp partitions on my "normal" SATA HDD.

Or is my assumption incorrect?

Ta,
X

---

### Post by Pumalite on 2008-05-04
I think the incorrect is I. I am not aware of your flash.

---

### Post by xenomorph99 on 2008-05-04
Hi,

It's been suggested that the IDE CF is reported incorrectly or the installer cannot deal with it correctly. 

Is there a way of fooling/modifying how this device might be seen to permit the "correct" kernel to be selected?

Ta,
X

---

