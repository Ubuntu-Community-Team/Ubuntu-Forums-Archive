---
title: "Ubuntu Install"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by PossumNZ on 2011-08-09
I have a eMachine laptop running Windows 7 and have Ubuntu 11.04 as a dual boot.
 
The  Windows 7 system has been effected with a Adware program which is very hard to remove also I don't want to keep Windows.

If I start a reinstall of Ubuntu and nominate Ubuntu as my only system on my laptop, will the install wipe clean the partitions made previous for Ubuntu and remove windows 7?
:)

---

### Post by Basher101 on 2011-08-09
Yes you get an option on the installer to replace your current OS. Simply select that and it will wipe your hdd clean and do a fresh install.

---

### Post by Mark Phelps on 2011-08-11
While I admire your enthusiasm to get away from Windows, you don't want to end up with NO working PC.  So, before you wipe out anything, boot from an Ubuntu Desktop PC, select the Try Ubuntu mode -- and see how well it works.

It will be slower because it's running from the CD, but it will give you a feel for the desktop interface and how well it detects all your hardware and installs the proper drivers.

Anything that does NOT work is going to present a problem after installation -- and these range from trivial (like installing restricted video/wifi drivers) to serious -- like finding a driver for hardware that Ubuntu simply does not detect (like special buttons and switches on laptops).

Also, if you do encounter problems when running the LiveCD, you can post back here or do forum searches -- and maybe have solutions lined up before you do the install.

---

### Post by sanderd17 on 2011-08-11
@Marc, the OP already has an Ubuntu Dual boot installation, so it will work with the hardware.

@PossumNZ: You don't need to reinstall Ubuntu. Just boot a live CD in try-mode, open Gparted, delete the windows partitions, enlarge the Ubuntu partition(s) (don't forget to apply the changes) and run

```

sudo update-grub

```

Do backup all important files. If you computer crashes for any reason while changing partitions, you can lose all data on your HDD.

**EDIT**

I assumed it was a normal dual boot and no Wubi installation in the above explanation. If it is a Wubi installation, than you need to reinstall Ubuntu.

---

### Post by YesWeCan on 2011-08-11
> **sanderd17 said:**
> @Marc, the OP already has an Ubuntu Dual boot installation, so it will work with the hardware.

@PossumNZ: You don't need to reinstall Ubuntu. Just boot a live CD in try-mode, open Gparted, delete the windows partitions, enlarge the Ubuntu partition(s) (don't forget to apply the changes) and run

```

sudo update-grub

```

Running update-grub is a good idea but it won't work from the live CD. Instead it will try to update the live CD's Grub installation, which it won't be able to do.

To do update-grub from live CD on the hard disk Ubuntu would require a chroot. This is doable but a little fiddly (see [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) section 12.1.4).

Anyhow, the update-grub can wait until the newly adjusted Ubuntu is rebooted.

Sometimes changing the Ubuntu partition and moving it will stop the already installed Grub from working properly. So as a precaution, after doing the GParted stuff on live CD, also reinstall Grub to the MBR: see link section 12.1.2.

---

