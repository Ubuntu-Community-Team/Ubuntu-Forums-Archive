---
title: "Problems running Virtualbox"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by zellbz on 2010-06-13
I am new to Ubuntu/Linux and I am having trouble running virtualbox 3.2. I have Win7 on a DVD and when i am about to start the installation in virtualbox it says that:
 "Kernel driver not installed (rc=-1908)
 
The virtualbox Linux kernel driver(vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall kernel module by executing { '/etc/init.d/vboxdrv setup } as root."

I went to terminal and wrote the command and nothing happened. can anyone help getting vbox installed on my machine?

edit: I am running Ubuntu netbook remix 10.04

---

### Post by lechien73 on 2010-06-14
Does the /etc/init.d/vboxdrv file exist? If so, then running:

```
sudo /etc/init.d/vboxdrv setup
```

from a terminal window should compile the kernel driver. If it doesn't exist, then you should try a complete removal and reinstall of VirtualBox.

Personally, I prefer using the PEUL version, available from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) rather than the OSE version installed from the repositories.

---

