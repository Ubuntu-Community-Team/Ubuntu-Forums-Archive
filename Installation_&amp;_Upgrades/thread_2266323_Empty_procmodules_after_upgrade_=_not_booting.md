---
title: "Empty /proc/modules after upgrade = not booting"
date: 2015-02-21
forum: Installation &amp; Upgrades
---

### Post by craig41 on 2015-02-21
I am new to kernel compilations in Ubuntu.  The development system is running 14.04.1 and I have succeeded in making the .deb file (fakeroot make-kpkg --initrd kernel-image kernel-headers modules_image).  To have a nice clean install environment, the target system gets a fresh install of 14.04, I copy the .deb files (linux_header* and linux_image* files) to the target system's hard drive, and install the .deb files.  (I've done installs via both the gui interface and the dpkg at the command line.)  The installs work fine.  When booting to the new kernel, however, the boot process noticably pauses and then I get:

Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
Alert!  /dev/disk/by-<long hex string I won't retype> does not exist.
Dropping to a shell!

The UUID for the new install is identical to the UUID that grub knows for the original install.  When checking it from the shell, it turns out the /proc/modules file is empty.  How do I get the modules to be part of the installation or how do I get the new kernel to use the modules that are already on the system?

Craig

---

### Post by MAFoElffen on 2015-02-21
/proc/ is created and managed by kernel... I think what you are looking for that is relevent to what is happening is here in the Debain doc's:
[https://www.debian.org/doc/manuals/debian-reference/ch03.en.html#_the_kernel_module_initialization](https://www.debian.org/doc/manuals/debian-reference/ch03.en.html#_the_kernel_module_initialization)

---

### Post by craig41 on 2015-02-22
Thanks for the reply, MAFoElffen.  I'm familiar with the notion of modules along with the modprobe, lsmod, insmod, etc., commands.  What I don't understand is why the second kernel (the one I've installed via the .deb file) can't find any modules.  What should I be adding to the make-kpkg command to bring the other modules along or to use what is there?  (I haven't changed anything that would impact the usability of the existing modules with the new kernel.)

Thanks.

---

### Post by MAFoElffen on 2015-02-22
Usually, your LKM's are installed into /lib/modules/<kernel_version>, in subdirectories under that... each one of those directories has it's own copy of all the LKM's. From there, when the specific version of a kernel loads, it populates the /proc/modules from those, as they are loaded.

---

