---
title: "Installation without reboot"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by thezood on 2011-08-20
Does anyone know if it's possible to install Ubuntu without rebooting the machine?

For instance, I'm just now going to install Oneiric on a separate partition to try it out but what's the point with having to reboot onto a USB disk? I think I could just as well install it without having to rebooting my machine, since I'm not going to make any changes to my current operating system.

---

### Post by Quackers on 2011-08-20
Installing Ubuntu will put grub in the mbr of the hard drive over-writing what's already there, so changes are being made to your existing system.
When rebooting after installation you take out the Ubuntu cd/usb first, to boot the installed system - you are aware of that?

---

### Post by sanderj on 2011-08-20
> **thezood said:**
> Does anyone know if it's possible to install Ubuntu without rebooting the machine?


Yes, that's possible. I see the following ways to do that:

[LIST]
[*]Install Ubuntu via wubi (assuming you're running Windows)
[*]Install Ubuntu onto an USB stick using a usb-stick-program for your OS (Windows or Linux)
[*]Install Ubuntu in a Virtual Machine on your current OS.
[/LIST]

No need to reboot when installing this way.

> **thezood said:**
> 
For instance, I'm just now going to install Oneiric on a separate partition to try it out but what's the point with having to reboot onto a USB disk? I think I could just as well install it without having to rebooting my machine, since I'm not going to make any changes to my current operating system.

I don't understand this: 
[LIST]
[*]how can you install Linux onto a separate harddisk partition without (re)booting that Linux to get the harddisk install program at all? Do you have a special tool for that?
[*]why would install you onto a partition **and **use a USB stick/disk?
[/LIST]

---

### Post by thezood on 2011-09-27
Bumping this since I still feel it's a good idea. The previous two posts completely misunderstood my idea.

I want to be able to install Ubuntu to an (of course) unused partition **without** using an USB device. This would require a special installation tool that copies the contents of an ISO directly to a partition and configure it, without the need for a reboot into an installation environment. It would be perfect if you (like me) have several Linux partitions running simultaneously and want to avoid the hassle of preparing a USB drive for every installation.

No, it's not super-important. It would simply be nifty for us lazies.

---

### Post by garvinrick4 on 2011-09-27
> No, it's not super-important. It would simply be nifty for us lazies.To Lazy, going to want a live cd or Usb incase of any needed repairs Burn a cd with .iso
or make a USB. 10 to 15 minutes and if it is a USB do not use persistence will be quick.

---

### Post by thezood on 2011-10-06
> **garvinrick4 said:**
> To Lazy, going to want a live cd or Usb incase of any needed repairs Burn a cd with .iso
or make a USB. 10 to 15 minutes and if it is a USB do not use persistence will be quick.

It's not just laziness. I just think it's an unnecessary step and it's a relic from the times when you needed an installation medium. This is no longer the case but all operating systems cling to the old ways using disk images and reboots which is really unnecessary. But I guess I'm ahead of times as usual. It's not easy being a renaissance man.

---

### Post by sisco311 on 2011-10-06
I usually use debootstrap. [uhelp]community/Installation/FromLinux#Without_CD[/uhelp]

---

### Post by thezood on 2011-10-07
> **sisco311 said:**
> I usually use debootstrap. [uhelp]community/Installation/FromLinux#Without_CD[/uhelp]

Brilliant, thanks.

---

