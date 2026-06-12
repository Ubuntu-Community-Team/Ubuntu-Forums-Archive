---
title: "no USB no CD install"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by Raddish on 2012-11-21
Hi,

I have a laptop which is unable to boot from USB (Bios limitation)
it also cannot read CD-Rs or any "home burnt" disks - it reads "factory" disks fine.

From some searching it would seem that I can install Ubuntu from the network - either from a local server (PXE?)on a machine here or from files on the internet - this is if I can create a linux bootable partition on my hdd & install grub to it, add/change some files and re-boot into a ramdisk which will then launch the ubuntu installer over the internet.

I'd prefer not messing with other machines locally to set up a install server so I'd prefer the internet solution.

The laptop has windows xp currently - I want to replace this with Ubuntu 12.04 (probably)

How do I create a linux partition (which flavour?) & install grub to it from within windows?

How do I then edit/replace the required files for the ramdisk boot?

I could really do with some pointers here please

Cheers

---

### Post by Androzani1 on 2012-11-21
You could try buying a pre burned disk over the internet, it costs a bit but is much easier.

---

### Post by Raddish on 2012-11-23
Thanks for the suggestion but I don't give in that easily! The thought had occurred to me if I get really stuck tho!

As of now I have installed Wubi - used this to create new linux partition & swap partition -  migrated my Wubi installation to to these new partitions as a bootable OS - uninstalled Wubi from wndows.

So I now have a dual boot XP & 12.04 system which is a major step forward \\:D/ - I might just live with that for now allthough I'd like to -

Remove windows & NTFS partition completely,
create a new bootable Grub partition in its space
configure this grub to able to boot either the installed OS (12.04 as it would be now) OR boot to a ramdisk & get & install distro from net

Any ideas/ pointers please?

Cheers
  C

---

### Post by 2F4U on 2012-11-23
A PXE install requires an install server.

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)
[https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

If you don't want to setup an install server, you would need a netinstall cd/usb, but since this doesn't work on your machine, netinstall is not an option.

---

### Post by cwsnyder on 2012-11-23
One other potential problem with PXE boot, it must be supported and enabled, either in your BIOS or your network adapter for it to work.  You would be better off to see if you could boot from either an external drive, internal CD or thumb drive with Plop bootloader, which can be installed from a floppy.  Do you have an internal floppy?

---

### Post by Raddish on 2012-11-24
I have a network boot option in my laptops bios - so I hope PXE is an option if I need.
Internal CD does not read home burnt disks & laptop cannot boot to USB & no floppy.

My understanding was that I can boot from the hard disk into a ramdisk to leave the HDD available for the install which can be run over the net -

Here - 
[https://help.ubuntu.com/12.04/installation-guide/i386/boot-drive-files.html](https://help.ubuntu.com/12.04/installation-guide/i386/boot-drive-files.html)

Is this right or have I misunderstood?

---

### Post by cwsnyder on 2012-11-24
That is right.  I have seen the method, but never tried it.

---

### Post by Cheesemill on 2012-11-25
In situations like this I usually just pull the hard drive and put it in a machine with a working CD to do the installation, then replace it in the original machine once it has the OS installed.

---

