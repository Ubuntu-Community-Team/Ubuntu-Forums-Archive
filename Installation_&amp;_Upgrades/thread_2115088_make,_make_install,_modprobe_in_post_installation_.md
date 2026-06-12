---
title: "make, make install, modprobe in post installation script"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by Anaximander Thales on 2013-02-11
I modified a post installation script for nvidia, [found here]("http://ubuntuforums.org/showthread.php?t=835573"), for installing the Ceton InfiniTV drivers.  This -- this has become a learning situation for me as it does not work as expected.

Here is the script:
```

#!/bin/bash
#
 
# Set this to the exact path of the ceton infinitv driver you plan to use
# It is recommended to use a symlink here so that this script doesn't
# have to be modified when you change driver versions.
DRIVER=/usr/src/ceton_infinitv_linux_driver
 
 
# Build new driver if it doesn't exist
if [ -e /lib/modules/$1/extra/ctn91xx.ko ] ; then
    echo "CETON infinitv drivers already exists for this kernel." >&2
else
    echo "Building CETON infinitv driver for kernel $1" >&2
    cd $DRIVER
    /usr/bin/make 
    /usr/bin/make install
    /sbin/modprobe ctn91xx

    if [ -e /lib/modules/$1/extra/ctn91xx.ko ] ; then
        echo "   SUCCESS: Driver installed for kernel $1" >&2
    else
        echo "   FAILURE: See log for issues" >&2
    fi
fi
 
exit 0

```

I hoped that the script would install the ceton drivers when a new kernel was installed.  However, what occurs is it attempts to install the drivers on the current kernel.

```
Building CETON infinitv driver for kernel [COLOR=red]3.2.0-38-generic[/COLOR]
make[1]: Entering directory `/usr/src/linux-headers-[COLOR=blue]3.2.0-37-generic[/COLOR]'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-[COLOR=blue]3.2.0-37-generic[/COLOR]'
Installing ctn91xx driver...
make[1]: Entering directory `/usr/src/linux-headers-[COLOR=blue]3.2.0-37-generic[/COLOR]'
  INSTALL /home/user/Downloads/ceton_infinitv_linux_driver/ctn91xx.ko
  DEPMOD  [COLOR=blue]3.2.0-37-generic[/COLOR]
make[1]: Leaving directory `/usr/src/linux-headers-[COLOR=blue]3.2.0-37-generic[/COLOR]'
cp 98-ctn91xx.rules /etc/udev/rules.d/
/sbin/depmod -a [COLOR=blue]3.2.0-37-generic[/COLOR]
   FAILURE: See log for issues
```

My question is, how do I make this work as a post installation trigger?

Thanks,
AT

---

### Post by Anaximander Thales on 2013-02-14
Bump

---

### Post by schragge on 2013-02-14
Do you have the package *linux-headers-3.2.0-38-generic* installed?

---

### Post by Anaximander Thales on 2013-02-14
> **schragge said:**
> Do you have the package *linux-headers-3.2.0-38-generic* installed?

In theory, yes -- I can't be 100% certain because at the point the script runs it's still running through the upgrade process.

However, This post install script should run when a kernel update occurs, it should kick off after the kernel is installed.  In apt output messages, it checks whether it has been installed for the new kernel or not (the new kernel is checked, and it shows that the driver hasn't installed) and attempts to install for the new kernel, however, when make, make install and modprobe run, they attempt to run against the previous kernel.

---

### Post by schragge on 2013-02-14
I guess then your should use dkms and invoke it from your postinst.

---

### Post by Anaximander Thales on 2013-02-14
> **schragge said:**
> I guess then your should use dkms and invoke it from your postinst.

I am invoking it from postinst (script is located in /etc/kernel/postinst.d as stated in the article that I linked to about the original script).

DKMS I am unfamiliar with.

I'll follow this guide ([Ubuntu Community - DKMS]("https://help.ubuntu.com/community/DKMS")) and report how it goes.  

Just a quick read through, it doesn't mention anything about postinst.  I am assuming that this part of the DKMS doc:
[QUOTE=DKMS DOC]we install the module into DKMS by copying the module installation files into the kernel source tree /usr/src/<modulename>-<version> and tell DKMS about the new module:[/QUOTE]
means that after I do that, it'll set up a postinst trigger for when a new kernel is installed.  Am I correct in that or
will I need to put the dkms.conf file in the postinst.d directory, or modify my script in some way to make this work? 

Thank you,
AT

---

### Post by schragge on 2013-02-14
Also look [here]("https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging").

---

### Post by Anaximander Thales on 2013-02-14
Thank you, schragge

When I get home I'll test it out and report back on it.

Thanks,
AT

---

### Post by Anaximander Thales on 2013-03-02
Okay -- 
Implemented DKMS -- 

It worked.

Much thanks to schragge.

---

