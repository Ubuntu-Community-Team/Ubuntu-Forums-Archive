---
title: "Barebones Ubuntu install possible on partitioned hard drive?"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Bart_D on 2007-08-18
I am planning to do an installation of Ubuntu minimal but have several partitions on my hard disk.  Will I be able to specify which partition I want to install it to or does it just do a generic install and wipe out everything on the disk?

I will be following these instructions:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by merlinus on 2007-08-18
Also look at this:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

-merlin

---

### Post by Bart_D on 2007-08-18
> **merlinus said:**
> Also look at this:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

-merlin

Thanks, but I have two questions.  

1.  With the second link, I won;t actually be using the Alternate CD right....I mean I will be using the Minimal CD shown here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

The reason why I ask is because (TO MY UNDERSTANDING...BEGINNER HERE) it goes SOMETHING like this:

- the Alternate CD actually installs the system with packages
- the Minimal CD requires the user to install the packages from a terminal

2.  Will I still get the option of creating partitions of the desired types with the minimal CD or would this have to be done with Gparted or the like?

Ok, 3 questions:
2.  HARDWARE RELATED:  Can a hard drive connected as "SLAVE" be used to install and run Ubuntu?

---

### Post by aysiu on 2007-08-18
I believe the minimal CD has the same installer interface as the alternate CD, so the Herman link will help, and you will have the option to repartition during installation.

---

### Post by logos34 on 2007-08-18
> **Bart_D said:**
> 2.  HARDWARE RELATED:  Can a hard drive connected as "SLAVE" be used to install and run Ubuntu?

Yes.  Just be sure to install to drive 'hdb', and if you don't want Grub bootloader on hda (maybe you have windows and would prefer to keep it untouched) and would rather boot to Grub on hdb, then be sure to specify that Grub be installed to 'hd1' or use '/dev/hdb'

---

### Post by jim_p on 2007-08-19
> - the Alternate CD actually installs the system with packages
- the Minimal CD requires the user to install the packages from a terminal

The Minimal cd downloads and installs everything from the net.
In any other aspect, the interface is identical to the Alternative install cd.

---

### Post by Bart_D on 2007-08-19
In the first link...the one I posted in the first post....it shows how to go through a lot of steps from the terminal environment and have to CREATE a desktop environment...am I missing something?

If not, then waht is the real difference between Minimal CD and Alternate CD?

---

### Post by aysiu on 2007-08-19
> **Bart_D said:**
> In the first link...the one I posted in the first post....it shows how to go through a lot of steps from the terminal environment and have to CREATE a desktop environment...am I missing something?

If not, then waht is the real difference between Minimal CD and Alternate CD?
Minimal will always install only the minimal.

The Alternate defaults to installing a full graphical environment with a lot of software packages, but you can override that.

So both can give you a barebones installation. The advantage of the minimal is that it takes less time to download than a 700 MB .ISO.

---

### Post by Bart_D on 2007-08-20
> **logos34 said:**
> Yes.  Just be sure to install to drive 'hdb', and if you don't want Grub bootloader on hda (maybe you have windows and would prefer to keep it untouched) and would rather boot to Grub on hdb, then be sure to specify that Grub be installed to 'hd1' or use '/dev/hdb'

I currently have XUbuntu and Zenwalk installed on hda.  Now, how would I get the boot loader to show ALL distros installed i.e. all the distros from BOTH hard drives?  No Windows installation.  I would like to be able to choose from all of them.

---

