---
title: "Unetbootin LiveCD image onto HDD?"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by c-m on 2010-10-27
My old HDD died. I have 10.10 installed on a usb stick. This is a full installation not a LiveCD.

I downloaded the live CD and Unetbootin.

Can I use unetbootin to create a bootable 'LiveCD' onto a partition of my new hard drive?

Without a CD drive, I can't think of any other way to get an installation onto my new HDD


EDIT - got ubuntu installed but had to do it at work, so i am still curious as how one would proceed with only a USB (full installation) and a blank HDD with no access to any other computers.

---

### Post by C.S.Cameron on 2010-10-27
You can install to your new HDD using a Live USB made with UNetbootin.

You can clone your Full install USB stick to your new HDD using dd.

You can stick your new HDD into a second computer and install Ubuntu, then move it back into the original computer.

If you have Windows on your new HDD you can use Type: Hard Disk option to run install next time you boot.

---

### Post by c-m on 2010-10-27
This computer has only, the new HDD and the USB stick. 

The usb stick is a single partition full installation.

There is no access to Windows nor any other machines.

First I thought i might be able to use Ubuntu's statup disk creator and have it make /dev/sda1 an ubuntu start up disk.

It turns out the startup disk creator can only work with USB sticks.

Secondly i downloaded an image and tried using unetbootin to make /dev/sda1 a 'live' linux startup disk. While unetbootin told me it successfully finished the job, up on restarting, the new disk could not locate the vmlinux (or something similar).


Cloning would have been great, but then i guess i would have had to manually recreate the boot loader and set a boot flag on sda1

Any other advice

---

### Post by meoconvn38 on 2010-10-27
> **c-m said:**
> My old HDD died. I have 10.10 installed on a usb stick. This is a full installation not a LiveCD.

I downloaded the live CD and Unetbootin.

Can I use unetbootin to create a bootable 'LiveCD' onto a partition of my new hard drive?

Without a CD drive, I can't think of any other way to get an installation onto my new HDD

*Sure download the iso file to "some computer" then install unetbootin and create live boot.Please remember sot set the cmos for boot usb first.*I used to do like this when my hard disk broken.:)

---

### Post by C.S.Cameron on 2010-10-28
When you clone with dd, if the cloned drive is bootable the target drive will also be.

---

