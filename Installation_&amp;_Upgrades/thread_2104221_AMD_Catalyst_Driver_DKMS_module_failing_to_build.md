---
title: "AMD Catalyst Driver DKMS module failing to build"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by Mercee on 2013-01-12
Hi all, I have a Toshiba Satellite running Xubuntu 12.10 x86_64. Yesterday I went to install the fglrx package using APT (without realizing it was a bad idea), rebooted, and the X server didn't want to start up; here's the error log:

```
...
Loading extension GLX
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
SetVBEMode failed

Fatal server error:
no screens found
(EE)
Please consult The X.Org Foundation support
        at http://wiki.x.org
 for help.
Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
```
/var/log/Xorg.0.log: [http://ompldr.org/vaDFnbw]("http://ompldr.org/vaDFnbw")

So I then disabled the extension (by running "sudo jockey-text -d kmod:fglrx") and uninstalled it.

After asking on Ask Ubuntu, I was told to install fglrx manually, so I went ahead and tried to install it by following the instructions in [this post]("http://askubuntu.com/a/129200"), however during installation, the installer is unable to build the DKMS module. Here's logs:

```
Created directory fglrx-install.rUnXwA
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.98...
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 6.9 or later 64-bit
loki_setup: directory: (null)
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
Removing temporary directory: fglrx-install.rUnXwA
```

And /usr/share/ati/fglrx-install.log:

```
Check if system has the tools required for installation.
fglrx installation is being forced. Installation will proceed without the required tools on the system.
Uninstalling any previously installed drivers.

Creating symlink /var/lib/dkms/fglrx/8.98/source ->
                 /usr/src/fglrx-8.98

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.98/build; sh make.sh --nohints --uname_r=3.5.0-21-generic --norootcheck....(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-8.98 with DKMS
[Error] Kernel Module : Removing fglrx-8.98 from DKMS

------------------------------
Deleting module version: 8.98
completely from the DKMS tree.
------------------------------
Done.
```

Anyone know how I can fix this so I can install fglrx? Thanks!

---

### Post by 2F4U on 2013-01-12
The installation instructions ask to install these dependencies:

> sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases sudo apt-get install ia32-libs

Have you installed the packages before you tried to build the module?

---

### Post by Mercee on 2013-01-12
> **2F4U said:**
> The installation instructions ask to install these dependencies:



Have you installed the packages before you tried to build the module?

Yes, all those dependencies were already installed.

---

### Post by Mark Phelps on 2013-01-12
Toshiba satellites go back over 10 years, anything but the very newest is likely to have an AMD video chipset that will not run fglrx drivers under 12.10.  IF you have a chipset that is older than the HD 5x series -- you are out of luck.  The HD 4x series, and prior, require an older X-server version that is not in Ubuntu 12.10.

---

### Post by Mercee on 2013-01-12
> **Mark Phelps said:**
> Toshiba satellites go back over 10 years, anything but the very newest is likely to have an AMD video chipset that will not run fglrx drivers under 12.10.  IF you have a chipset that is older than the HD 5x series -- you are out of luck.  The HD 4x series, and prior, require an older X-server version that is not in Ubuntu 12.10.

It's a Toshiba Satellite C850D-11Q, to be exact, which looks fairly recent.

I think I have a 7x chipset, as this line appears in the X startup error log:

```
[  1322.782] (--) fglrx(0): Chipset: "AMD Radeon HD 7310 Graphics" (Chipset = 0x9809)
```

---

### Post by Mercee on 2013-01-13
Bump.

---

### Post by Mercee on 2013-01-15
Another bump. I found and followed [this installation procedure]("http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL"), however X still refuses to start with fglrx installed. Here's some logs:


Installation procedure: [http://ompldr.org/vaDJ3aw](http://ompldr.org/vaDJ3aw)

X error log with fglrx installed: [http://ompldr.org/vaDJ3bA](http://ompldr.org/vaDJ3bA)

X error log without fglrx installed: [http://ompldr.org/vaDJ3bQ](http://ompldr.org/vaDJ3bQ)

---

### Post by Mercee on 2013-01-16
bump

---

