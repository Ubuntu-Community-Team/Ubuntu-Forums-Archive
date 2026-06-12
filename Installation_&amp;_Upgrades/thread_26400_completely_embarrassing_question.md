---
title: "completely embarrassing question"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by fractalvibes on 2005-04-12
I have an old compaq PC with Windows ME on it.  Having always bought new machines with the OS pre-installed, I have no ideas of what steps are needed to get rid of the old OS and load Linux Ubuntu from the cd image of Ubuntu I downloaded to a new machine and burned.  Do I wipe the disk clean? Do I simply uninstall  windows?  Any advice as to the step by step I need to go through to accomplish this task will be most appreciated.

thanks,

fv

---

### Post by az on 2005-04-12
You put in the cd and boot from it.  If it does not boot, you reset and go into your bios (it will tell you which key to press to "enter setup" or something like that.   Usually it is F1 or del or something like that.  Be quick!
In the bios menu, look for boot device setting "boot order" and make the cdrom the first thing that it boots, followed by the hard drive.  Now, your computer will look for something to boot on the cdrom before booting from your hard drive.
Save and quit and you should not be booting from the cd.

Accespt the defaults and Ubuntu will erase your harddisk while putting itself on it.

You may dual-boot and keep the existing os.  You will need to shrink the partition on which it is to do that.  That works fine, too.  

You create free space and then tell the installer's partitioner to do guided partitionning.

---

