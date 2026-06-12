---
title: "Installing ubuntu on comp A using comp B"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by brianhillman on 2010-08-19
i have a bit of a situation here basically i cannot find out how i can get ubuntu installed on computer A ( laptop ) the problem is that it does not have a cd drive or support usb boot and the only way i have been able to acess the hard drive is by attaching it to comp B and browsing it

i have tried installing ubuntu onto it with comp B but cannot get it to boot with Comp A once installed. is there a way to copy over files and have it boot the installer directly from the hard drive?

---

### Post by oldfred on 2010-08-19
You should be able to boot it with comp a. Did you use the advanced button to be sure to install grub to comp A's drive? That should at least get you to boot. If you only have Ubuntu you will not get a menu and may have video issues. Use shift to get menu and e to edit Ubuntu entry and replace splash quiet with nomodeset or other parameters depending on your video drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

### Post by sanderj on 2010-08-19
First of all: your method with harddisk swapping should work. Does the harddisk correctly boot in machine B? And in machine C? Does machine A see the harddisk at all? What's the error message in Machine A?

Other methods:
- floppy drive (see [https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager))
- an external cd drive to boot from
- PXE boot (much harder)
- If it still has Windows use Wubi

HTH

---

