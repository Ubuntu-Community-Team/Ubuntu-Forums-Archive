---
title: "Error generating kernel module for Virtualbox"
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2014-08-11
I am on 12.04.5 x64.  A week or so ago, I upgraded my Virtualbox to 4.3.14 by downloading from the Virtualbox site.  Now that 14.04.1 is finally ready for upgrades, I removed 4.3.14 and reinstalled 4.1.12, the one that came with 12.04.  When I try to start my VM, I get the following message:> Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.When I try to reinstall the kernel module I get the following:```
 sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules/etc/init.d/vboxdrv: 302: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...done.
Trying to register the VirtualBox kernel modules using DKMS/etc/init.d/vboxdrv: 327: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)

```/var/log/vbox-install.log contains the following```
/etc/init.d/vboxdrv: 334: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/build_in_tmp: not found
```I installed virtualbox-source, but I do not have the directory /usr/share/virtualbox/src.  Anyone have any ideas?

---

### Post by TheFu on 2014-08-11
Install the required dependencies before attempting this. [http://blog.jdpfu.com/2012/07/05/virtualbox-guest-extension-dependencies](http://blog.jdpfu.com/2012/07/05/virtualbox-guest-extension-dependencies)

---

### Post by cscj01 on 2014-08-16
Closed after upgrade to Trusty.

---

