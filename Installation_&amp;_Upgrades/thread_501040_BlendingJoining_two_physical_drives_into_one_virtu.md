---
title: "Blending/Joining two physical drives into one virtual drive"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by Warren Watts on 2007-07-14
I have a system with two 5GB hard drives, currently set up as dual boot, with Edubuntu Workstation on one drive and Xubuntu on the other.  I set the system up primarily just to play around with both flavors of Ubuntu.

I have now settled on Edubuntu and I want to re-install Edubuntu Server only on the system, but I want to "blend" both drives into one virtual drive for the install.  How do I go about this?  Can I partition and "join" the drives during the install, or do I need to do something first?

---

### Post by jfinkels on 2007-07-14
> **Warren Watts said:**
> I have a system with two 5GB hard drives, currently set up as dual boot, with Edubuntu Workstation on one drive and Xubuntu on the other.  I set the system up primarily just to play around with both flavors of Ubuntu.

I have now settled on Edubuntu and I want to re-install Edubuntu Server only on the system, but I want to "blend" both drives into one virtual drive for the install.  How do I go about this?  Can I partition and "join" the drives during the install, or do I need to do something first?

You will need either RAID ([http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)) or LVM ([http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)) to stripe your data across multiple disks. You also will need a motherboard (and an operating system) with support for that kind of setup.

---

### Post by Warren Watts on 2007-07-14
> **jfinkels said:**
> You will need either RAID .. or ... LVM.  You also will need .... an operating system)...with support for that kind of setup.

So does Edubuntu (certainly an OS) have support for LVM?

And how would I go about setting up the virtual drive with LVM and then installing from the Edubuntu CD?

You have to pardon my ignorance here....

---

### Post by jfinkels on 2007-07-14
> **Warren Watts said:**
> So does Edubuntu (certainly an OS) have support for LVM?

And how would I go about setting up the virtual drive with LVM and then installing from the Edubuntu CD?

You have to pardon my ignorance here....

No need to apologize, friend.

I am afraid, though, that I have no experience setting up LVM! Hopefully someone else will come along, or use Google to help you out.

---

### Post by Warren Watts on 2007-07-14
Reading thru the LVM HOWTO, it looks like the process is pretty involved.  

- Building and installing a kernel module 
  (not TOO big a deal, I have managed to struggle thru that before)

- Executing a *TON* of CLI commands to define, structure, build, initalize, enable, and partition the virtual drive
  (Way beyond my capabilites to do properly and successfully)

  I'm actually surprised it is so complicated.  I installed Fedore Core 4 on a system several years ago with a virtual drive, and the installer did all the work for me.  But from reading it looks like Fedora is a "LMV Aware" Distro and Ubuntu is not.  

But, I'll take Ubuntu over Fedora any day.

I think I'll just partition the drives as separate physical drives and deal with it.

Thanks for your quick response though!  

Gotta love the Ubuntu Community.

---

