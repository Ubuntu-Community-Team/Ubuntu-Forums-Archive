---
title: "Should I put secure boot back on?"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by Frantic_Earthling on 2014-09-18
I have successfully installed 14.04 on an Asus G750 JZ.
Now the installation is complete and my dual boot works without a hiccup, should I put secure boot back on?
If I do, or if I do not, what do you think are the risks?

---

### Post by fantab on 2014-09-18
Enabling 'Secure Boot' after installing Ubuntu has sometimes worked and in some instances it didnt.
Did you try installing Ubuntu with 'Secure Boot' enabled? Usually, Grub with SHIM enables you to install Ubuntu with Secure boot enabled.
If you enable 'Secure Boot' and find ubuntu not booting then you will have to use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool to re-install Grub with SHIM keys...

[http://www.zdnet.com/shimming-your-way-to-linux-on-windows-8-pcs-7000008246/](http://www.zdnet.com/shimming-your-way-to-linux-on-windows-8-pcs-7000008246/)

IMO, its fine to boot without 'secure boot' enabled... don't fix if it aint broken.

---

### Post by Frantic_Earthling on 2014-09-18
> **fantab said:**
> Enabling 'Secure Boot' after installing Ubuntu has sometimes worked and in some instances it didnt.
Did you try installing Ubuntu with 'Secure Boot' enabled? Usually, Grub with SHIM enables you to install Ubuntu with Secure boot enabled.
If you enable 'Secure Boot' and find ubuntu not booting then you will have to use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool to re-install Grub with SHIM keys...

[http://www.zdnet.com/shimming-your-way-to-linux-on-windows-8-pcs-7000008246/](http://www.zdnet.com/shimming-your-way-to-linux-on-windows-8-pcs-7000008246/)

IMO, its fine to boot without 'secure boot' enabled... don't fix if it aint broken.

That is what I will do.
It ain't brocken.
I won't fix it.

And no, I did not install Ubuntu with Secure Boot enabled. I did not even know this was possible :cool:. I will bear that in mind for next time though. Thanks for the info. :)

---

### Post by oldfred on 2014-09-18
I consider Secure boot to be primarily marketing by Microsoft. 

They have had a major issue with virus and other security issues. So what better way to convince users that you have improved system than implement "Secure Boot" which in actuality has nothing to do with all the historical security issues.

There have been very few boot virus and the only major one was the one released by Sony for DRM purposes.
All BIOS based older systems have no secure boot, and they are the majority of systems still out there.

In the future we may all need secure boot, but for now it is not required. 

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

