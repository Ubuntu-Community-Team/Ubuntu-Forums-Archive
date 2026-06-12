---
title: "Installing old proprietary drivers for legacy ATI cards"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by twisted_steel on 2009-09-16
Has anyone been able to get the version 9.3 ATI fglrx drivers to install in Karmic?  My video card is no longer supported with the latest drivers; I have a Radeon Mobility 9600.  I guess it was only a matter of time as I've been using Ubuntu on here since 4.10 (Warty).

I first tried running the installation script (ati-driver-installer-9-3-x86.x86_64.run).  This gave me the following error:
```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-10-generic; make sure that the version is being
correctly set by --iscurrentdistro
```I was able to build a "jaunty" package after installing the *debhelper* and *cdbs* packages.  Unfortunately, I ran into a problem with the very first package (fglrx-kernel-source_8.593-0ubuntu1_i386.deb).  During the installation, I saw the following output:
```
(Reading database ... 140632 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 2:8.593-0ubuntu1 (using .../fglrx-kernel-source_8.593-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (2:8.593-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.31-10-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.593/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.31-10-generic (i686) first.
Done.
```The installation of that package supposedly worked despite the error.  I thought it would be a good idea to check before continuing and destroying some critical piece of my system.

Thanks! :KS

---

### Post by lithorus on 2009-09-17
You will find that it's quite difficult. The 9.3 doesn't support the latest kernel and will probably never do. Compared to nvidia they don't maintain a legacy driver for older chipsets and keep that up to date with new kernels, but it seems they leave it to the community driven driver "radeon" which is built into Xorg. If I were you I would try the "radeon" driver instead of fglrx. Suspend should also work better with that.

Is there anything in particular feature that you need from the fglrx driver?

---

### Post by Amaranth on 2009-09-17
This is not possible because X changed and the driver is not compatible. It may be possible to force it to run but you'll get no hardware acceleration.

---

### Post by lithorus on 2009-09-17
> **Amaranth said:**
> This is not possible because X changed and the driver is not compatible. It may be possible to force it to run but you'll get no hardware acceleration.
Oh, yeah also forgot about that. So even if you get the fglrx kernel module to compile/load. X won't allow you allow you to continue.

---

### Post by ELD on 2009-09-17
Looks like your best bet just became the open source drivers, which have come along way from what i hear...if your card is supported by that ;)

---

### Post by twisted_steel on 2009-09-17
Nice.  I guess that gives me an excuse to file bugs against the open source radeon driver.  Compositing seems to cause the whole computer to lock up.  This is reminiscent of a problem I had a while ago that caused the card to be blacklisted.

---

### Post by michealm on 2009-09-17
> **Amaranth said:**
> This is not possible because X changed and the driver is not compatible. It may be possible to force it to run but you'll get no hardware acceleration.

this is correct om my GFs PC she has a ATI X1300 Pro ATI card, and no driver support besides the radeon package. Which sucks that card runs smooth as a baby's butt under Linux.

---

### Post by ssri on 2009-09-19
> **Amaranth said:**
> This is not possible because X changed and the driver is not compatible. It may be possible to force it to run but you'll get no hardware acceleration.

You can always downgrade X to 1.5.x and install fglrx 9.3 that way.  However, the argument to do so in karmic is rather moot due to the fact that fglrx 9.3 does not support kernel versions above 2.6.28.

---

