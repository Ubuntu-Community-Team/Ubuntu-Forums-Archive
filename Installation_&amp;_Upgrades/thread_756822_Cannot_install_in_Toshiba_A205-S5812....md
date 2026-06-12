---
title: "Cannot install in Toshiba A205-S5812..."
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by Negrazo on 2008-04-16
Hello everyone:
I bought a brand new Toshiba Satellite A205-S5812 with Windows Vista Ultimate as the OS, a 160GB SATA HDD and 2GB in RAM.
I tried to install Linux Ubuntu 7.04, as a second OS, and apparently the installer doesn't recognize the SATA HDD because it throws an error message:

-PXE-E61: Media test failure.
-PXE-MOF: Exiting PXE ROM.

Any idea where my problem is and how to solve it?
Has anyone gone through something like this?

Any hint is welcome.

Negrazo.

---

### Post by nicedude on 2008-04-17
These two error messages are not related to a SATA HDD, you are getting these because your computer is trying to boot from your Ethernet Network connection instead of your HDD or CD/DVD.  

So you should enter your Bios setup ( in case you don't know how to do that, there will be a key you press when the computer is first started like F2, F1, DEL, ESCAPE - I am not sure for your laptop which one it is so try them all if you have to ) and change the systems boot order so that HDD & or the CD/DVD drive is set to boot before the Ethernet Network boots.  I use the following order usually.

1st boot device = CD or DVD drive
2nd boot device = HDD
3rd boot device = Ethernet 

That way if I need to use a boot CD to do something I just put it in the drive and it will boot first but  if no CD is in the drive the HDD will boot first.

If after you have HDD & or CD set to be first and second boot devices it still won't boot then you have a bigger problem, but you probably don't.

Also you should probably download the 7.10 Gutsy Gibbon Live Ubuntu CD to try as it will probably work better for you. Also some systems just won't boot the Live disks and thats why they have separate install disks for each version called Alternate Install, but these only work for installing Ubuntu on your HDD. Hope ths helps you figure out your trouble.

Later

---

