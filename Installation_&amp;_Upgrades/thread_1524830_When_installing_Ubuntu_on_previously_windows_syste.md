---
title: "When installing Ubuntu on previously windows system.."
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by sweetness46 on 2010-07-05
I have a HP laptop that I have had Windows Vista on for about two years. I am soon going to switch it over to Ubuntu. My question is can you safely use the Ubuntu installation process to delete the Windows partition along with all the programs and files it stores on the hard drive or should you first uninstall Windows manually and then, with a essentially blank computer, install Ubuntu?

---

### Post by marshmallow1304 on 2010-07-05
The Ubuntu installer can optionally format partitions and use the entire disk.  When you get to the "Prepare disk space" step, just select "Erase and use the entire disk".

---

### Post by hansdown on 2010-07-05
Welcome to the forum, sweetness46.

The ubuntu disk will overwrite everthing on the drive, if you choose "use entire disk".

WARNING: this will delete ALL data from the windows install.

Here is a good tutorial.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by aphatak on 2010-07-05
You can, indeed, use the Ubuntu installation process to wipe the disk clean and install Ubuntu.  When you start the installation, you should get a menu of choices;  you can have Ubuntu occupy the whole disk, reduce an existing (in your case, Windows) partition and use the freed space to install Ubuntu, or you can be the real macho man and do your own partitioning and formatting.
If you have a large enough disk, I should keep Windows Vista *and* Ubuntu on the machine, and select the OS at boot time.  That way, you can have your cake and eat it, too!

---

### Post by sweetness46 on 2010-07-05
[COLOR=black][FONT=Verdana]Thanks for all the speedy replies. I have used Ubuntu on many systems before and gone through the installation process, almost always using the "Erase entire disk" option. My question was more geared toward whether or not it was better for the computer to uninstall Windows manually and then install Ubuntu, or does it not make much of a difference? Thanks.[/FONT][/COLOR]

---

### Post by wilee-nilee on 2010-07-05
> **sweetness46 said:**
> [COLOR=black][FONT=Verdana]Thanks for all the speedy replies. I have used Ubuntu on many systems before and gone through the installation process, almost always using the "Erase entire disk" option. My question was more geared toward whether or not it was better for the computer to uninstall Windows manually and then install Ubuntu, or does it not make much of a difference? Thanks.[/FONT][/COLOR]

It's basically the same, the installer will erase the Windows partition the same as you would with another partitioner like gparted. Really the only thing not touched with a other then installer erase is the mbr, unless directed to do so, if it is an option, gparted doesn't have this option.

---

