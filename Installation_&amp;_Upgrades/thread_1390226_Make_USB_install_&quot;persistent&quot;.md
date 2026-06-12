---
title: "Make USB install &quot;persistent&quot;?"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2010-01-25
I have 64bit Ubu 9.10 installed and running on a 1GB flash drive (I'm using it now), which is a great emergency OS for when Windows breaks down. 9.10 gives me access to both my RAID-0 C: drive AND the data on Blu-ray disks (even XP can't do that).

The only drawback is that I must re-enter my preferences/settings every time I boot my USB copy of Ubu. **I've even been able to install WINE onto it** to run simple Windows apps. Love it. But it is beyond a nuisance to have to reinstall it with every use.

I searched online for ways to make my instillation "persistent" so that it stores all this info between uses, but every how-to I've read only explains how to do this from a FRESH install following a reformat.

It took me several attempts just to get Ubu installed and working on this Flash drive in the first place, and I fear if I reformat and install again, I won't get it back.

Is there a simpler way to make Ubu remember my settings short of a total reformat/reinstall? Thx.

BTW: If you need to know how to get WINE working on a Flash drive with 64bit Ubu, let me know. :)

---

### Post by phillw on 2010-01-25
Hi, 

A quick word of warning -- backup your pen drive !!!

The good people over at pendrivelinux do quite a wonderful set of things with & to pen-drives. For **creating** the casper r-w section (The bit that does the persistence) you'll need access to a Win machine for ease, that is covered here --> [http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/)

From what I read of the article, It is adding the casper **in addition to** a file system.
> **[COLOR=#800000]Note[/COLOR]**: If you did not create your Ubuntu, Xubuntu, Kubuntu or other Ubuntu derivative USB flash drive using our tutorials and related installers, you will most likely need to append persistent to your boot menu options. To do this,  At the Boot Menu, select your language, then press F6, then press ESC and add persistent to the boot string, then press Enter to boot.
 				 

If you're comfortable with partitioning disks, then you can boot via a LiveCD (or Gparted CD) and make a partition for the casper-rw - [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)  has the details of how to set up a casper-rw partition.

Regards,

Phill.

---

### Post by Mugsy323 on 2010-01-25
> **phillw said:**
> For **creating** the casper r-w section (The bit that does the persistence) you'll need access to a Win machine for ease, that is covered here --> [http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/)

If you're comfortable with partitioning disks, then you can boot via a LiveCD (or Gparted CD) and make a partition for the casper-rw - [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)  has the details of how to set up a casper-rw partition.
Hi Phill, major thanks for the reply.

For whatever reason, the Windows app on pendrivelinux.com crashes when I try to run it in XP. No idea why.

The Wiki link requires a copy of the ISO on the same drive for it to work. Since this is just a 1GB drive, that's not an option.

I'm going to just go ahead and start from scratch using the Ubu9 USB app in the BootCD. Wish me luck. :)

---

