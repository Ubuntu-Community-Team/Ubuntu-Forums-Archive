---
title: "Old VirtualBox Kernel Drivers"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by philchambers on 2014-02-11
I have just been clearing out old linux-image and linux-headers files using 'dpkg -P ...'.  I then went to /lib/modules to see if anything remained and found quite a few old directories.  These all contain just a misc sub-directory in which there are: vboxdrv.ko, vboxnetadp.ko, vboxnetflt.ko and vboxpci.ko.

I presume I can just delete all these old files but would appreciate it if anyone can confirm this ore suggest a more appropriate way of removing them.

---

### Post by slickymaster on 2014-02-14
VirtualBox actually needs to install a kernel module for itself. DKMS is what handles the insertion and removal of kernel modules such as the Virtualbox ones when kernels are installed or removed.
Without being completely sure I would say that it's safe for you to delete them, but you should probably wait for some more feedback from others.

---

### Post by philchambers on 2014-02-19
Thanks for responding slickymaster.

After Update Manager installs a new kernel headers and such like, Virtualbox Manager refuses to start VMs and requires the kernel modules to be recompiled.

I use 'sudo /etc/init.d/vboxdrv setup' to do this and I have never had a problem, but it looks as if it does not remove the old files.

It would be nice to get confirmation though before I remove them manually.

---

### Post by SeijiSensei on 2014-02-19
There should be a vboxdrv.ko under /lib/modules/$(uname -r) for each bootable kernel.  Any ones associated with kernels you have deleted can be safely deleted as well.

---

### Post by philchambers on 2014-02-26
Thanks for responding SeijiSensei, you have confirmed what I thought was the case.  I have moved the redundant files to /tmp and the system still boots OK and VirtualBox still works fine.

---

