---
title: "Remote install from ISO"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by kihjin on 2008-08-03
I've been trying to figure out how I could do the following:

I've got a remote machine that has Ubuntu 8.04 installed. The machine is currently running in that operating system. I'd like to run the installer and setup another Ubuntu 8.04 directly from the ISO onto a separate partition. Without rebooting.

The remote machine does not have X11 and I'm connecting via SSH.

There has got to be a way to do this.

---

### Post by Pumalite on 2008-08-03
This might be useful:
[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

### Post by kihjin on 2008-08-03
Hi Pumalite,

I did come across that thread in my search of the forums. That HOWTO requires that I have physical access to the machine-in-question during it's reboot phase. 

What I HAVE been trying to do is use bochs to boot the ISO in a virtual machine, and install it to a partition on the main disk. However, bochs is so unbelievably slow that I'm still waiting for it to get to the partitioner. Plus it ties up my entire local machine when I run it since the svga library takes control of the entire screen.

Another avenue I've considered is using a kickstart file. I could edit the default boot entry to load a kickstart file from the internet. However, when the machine reboots it'll load back into the installer, since I don't know of a way to successfully revert the boot file after install.

---

