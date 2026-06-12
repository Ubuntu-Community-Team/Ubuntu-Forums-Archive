---
title: "Installation problem"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by Harrison McCray on 2008-07-05
Installing xubuntu 8.04 on 1997 Toshiba Lap Top.  Clean 800 MB hard drive. Get the following message, "ACPI: no DMI BIOS year, acpi=force is required to enable ACPI".  I entered acpi=force at the end of the line which comes up when you enter F6.  Still have problem.  What next?

---

### Post by overdrank on 2008-07-05
> **Harrison McCray said:**
> Installing xubuntu 8.04 on 1997 Toshiba Lap Top.  Clean 800 MB hard drive. Get the following message, "ACPI: no DMI BIOS year, acpi=force is required to enable ACPI".  I entered acpi=force at the end of the line which comes up when you enter F6.  Still have problem.  What next?

HI and welcome, well the first issue that I see is the 800mb hard drive will not be large enough for xubuntu. 
Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

---

### Post by Harrison McCray on 2008-07-05
Where can I find the system requirements for each version.  I thought I had enough memory for xubuntu.  Also, what is the meaning of the error message I received?:

---

### Post by overdrank on 2008-07-05
> **Harrison McCray said:**
> Where can I find the system requirements for each version.  I thought I had enough memory for xubuntu.  Also, what is the meaning of the error message I received?:

HI and you can find the system requirements here
[http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition)
If that was a typo on the 800mb hard drive and you meant 800mb of memory then you system should work. What are the system specs?
As for the error I can not help as I have not encounter such.

---

### Post by Harrison McCray on 2008-07-06
Thank for your responce.  I am still at a standstill on installing xubuntu.  It will install ok on my table top, I really want it on my old laptop!

---

### Post by logos34 on 2008-07-06
But what are your system specs?  Ram?  hard disk size?  because unless '800 mb' for hard drive is a typo, you can forget any version of ubuntu (alternatively try puppylinux, delininux, basiclinux, etc)

---

### Post by Habbit on 2008-07-06
800 MiB for a 1997 _laptop_ is pretty big, since in 1996 I got a Pentium 100 with a 850MiB Quantum Trailblazer. And yeah, you will most probably not be able to run Xubuntu on that... Maybe Fluxbuntu? If not, Gentoo might do the trick if you keep the Portage tree in another computer or an external hard drive.

---

### Post by snowpine on 2008-07-06
> **Habbit said:**
> 800 MiB for a 1997 _laptop_ is pretty big, since in 1996 I got a Pentium 100 with a 850MiB Quantum Trailblazer. And yeah, you will most probably not be able to run Xubuntu on that... Maybe Fluxbuntu? If not, Gentoo might do the trick if you keep the Portage tree in another computer or an external hard drive.

Fluxbuntu will not work on an 800 mb hard drive; it needs about 2 gb. Check out DSL (Damn Small Linux).

---

### Post by Bucky Ball on 2008-07-07
Damn Small Linux is what you're after. Xubuntu is also great but maybe sluggish with your setup.

Try this,
When you boot and you are looking at the grub menu, you have a few options if you check the bottom of that page. Hit 'e' to edit the boot you want.

Find the kernal line and at the end put this ...

noacpi

Hit return the 'b' to boot and see how you go. Try this page ...

[https://wiki.ubuntu.com/HP_dv6000_Series](https://wiki.ubuntu.com/HP_dv6000_Series)

I had no probs with 'noacpi' and 'nolacpi' stopping any devices, usb or otherwise. Good luck.

---

