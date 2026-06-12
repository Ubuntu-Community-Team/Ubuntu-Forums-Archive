---
title: "Problems installing Xubuntu 7.04 on a laptop"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by Slackersrule on 2007-06-02
I have an IBM X20 laptop, and I get MD5 validation errors on install.  The laptop itself doesn't have a CD Drive, so I am using the optional dock.

I have tried several different downloaded images, and they all do the same thing, so i'm pretty sure the image is fine.  The disc also works fine in other computers, just not this laptop.  The disc checker also gives me errors only on this laptop.

I'm not sure what I should do, this laptop doesn't boot from any other type of drive except hard drive and floppy.  Does anyone know if this could possibly be remedied?  

Also, if not, how would I go about doing a network install?  Could I also copy the files onto the hard drive somehow and run the install from there?

Thanks,
-Slacker

---

### Post by Slackersrule on 2007-06-02
Here's the error message I get first, every file after it is corrupt.

[ ! ! ] Install the base system
Debootstrap warning
Warning:
file:///cdrom/pool/main/k/klibc/klibc-utils_1.4.30-3ubuntu2_i386.deb was corrupt

<Go Back>                                       <Continue>

---

### Post by Gagle on 2007-06-02
Try running a MD5 CheckSum on the downloaded images to see if the download itself could've corrupted the file.

As for alternate install methods, you can install Edgy on a LAN using a PXE boot capable bios and a properly setup remote client.  A quick google and you will find the needed documentation.

If not VectorLinux has interesting alternate installation methods, from another OS for instance.

Nonetheless, I woulds start off by assuring myself that the MD5 check is passed.

Hope it helps,

Gagle

---

### Post by Slackersrule on 2007-06-03
I just checked the MD5 value, and it all checks out.

I guess I'll try the network stuff then :/

Could I possibly load an ISO image off of the hard drive using the installer, or some other program?  I can easily access the hard drive via a USB adapter.

---

