---
title: "fglrx failed with DKMS"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by Pazau on 2014-07-15
Hey all.

I have tried over several days to install the ATI drivers 13.1 on a machine with Ubuntu 12.04 64-bit and a ATI Radeon HD4890 without it so far succeeded. 

I have read a hell lot of guides around the web with no luck, so now I try here. 

A lot af guides told me to install the dependencies first: 
```
sudo apt-get install dbs fakeroot build-essential dh-make debconf execstack dh-modaliases debhelper dkms libqtgui4 libstdc++6 libelfg0 unzip ia32-libs-multiarch i386 lib32gcc1 ia32-libs libc6-i386
```

Then I download the driver manually and install.

I get the first error  that ```
/usr/lib/modules/<kernel_number>/build/include/linux/version.h
``` is missing - resolved by copying the file from ```
usr/include/linux/
``` 

First problem solved. 
Next: The 'famous' DKMS error

From fglrx-install.log:
```
Check if system has the tools required for installation.
Uninstalling any previously installed drivers.

Creating symlink /var/lib/dkms/fglrx/8.97.100.7/source ->
                 /usr/src/fglrx-8.97.100.7

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.97.100.7/build; sh make.sh --nohints --uname_r=3.11.0-24-generic --norootcheck.....(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-8.97.100.7 with DKMS
[Error] Kernel Module : Removing fglrx-8.97.100.7 from DKMS

------------------------------
Deleting module version: 8.97.100.7
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs
```

The driver does not support kernel higher than 3.2.* and X.org higher than 1.12.

These requirements are met:

```
X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Current Operating System: system_name 3.11.0-24-generic #42~precise1-Ubuntu Fri Jul 4 21:22:54 UTC 2014 x86_64
```


I have tried installing the driver by packaging .debs via this guide:
[http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html](http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html)

The installation succeeds with no erros; However, the fglrx module won't load, and ```
fglrxinfo
``` gives me an BadRequest error.

I have now hit a wall. 

Some suggestions to get the driver to install?

Thanks in advance!
- Nicolas

---

### Post by slooksterpsv on 2014-07-15
Kernel version UP TO 3.4 is support only. You'll either need to find a 3.4 kernel and downgrade to it or just use the xorg drivers that are installed by default. AMD dropped support pretty quickly for some of those graphics cards.

---

### Post by Mark Phelps on 2014-07-15
> and a ATI Radeon HD4890 without it so far succeeded.

Sorry, but you're not going to have success doing that -- because AMD dropped fglrx support for their HD 4x-series cards last summer.  The latest Ubuntu version that can use the fglrx drivers compatible with your card is version 12.04.1.  Newer Ubuntu versions come with an X-server that is incompatible with the HD 4x-series fglrx drivers.

---

