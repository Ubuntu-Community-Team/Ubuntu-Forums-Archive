---
title: "ubuntu help me to install ,in the same ssd with w7 installed and grub on usb"
date: 2014-10-24
forum: Installation &amp; Upgrades
---

### Post by ramas2 on 2014-10-24
hi
i really love ubuntu , i download the last built 64bit
i create an unlocated partition 80gb on my disk
i have w7 64bit on it

i would love to install ubuntu in this partition and the grub load in a usbstick

because i don't want to mess up my system
i would like to start my laptop with w7 and when i want to boot ubuntu ,plug the usb stick and via bios boot from the usb stick and boot ubuntu

in the installation wizzard there is no way to install the grub on my usb stick

please help , i'm a novice

---

### Post by Mark Phelps on 2014-10-24
We're mixing terms, which is confusing.  There is no such thing as an "unallocated partition". A partition is ALLOCATED space; unallocated space is space OUTSIDE of any partition.

When you install to unallocated space, the installer creates a partition for that install.

If you want to boot from USB stick, your best course of action would be to install TO a USB stick -- and to make sure that the Win7 MBR is not overwritten, have the hard drive disconnected when you do the install.

If you created a partition on your drive with Win7 to use for Ubuntu, and want to install to that instead of a USB stick, then REMOVE that partition -- as partition should be done with the Ubuntu installer, not with Win7.

---

### Post by ramas2 on 2014-10-24
> **Mark Phelps said:**
> We're mixing terms, which is confusing.  There is no such thing as an "unallocated partition". A partition is ALLOCATED space; unallocated space is space OUTSIDE of any partition.

When you install to unallocated space, the installer creates a partition for that install.

If you want to boot from USB stick, your best course of action would be to install TO a USB stick -- and to make sure that the Win7 MBR is not overwritten, have the hard drive disconnected when you do the install.

If you created a partition on your drive with Win7 to use for Ubuntu, and want to install to that instead of a USB stick, then REMOVE that partition -- as partition should be done with the Ubuntu installer, not with Win7.

Thanks Mark
well i created an unallocated space to install ubuntu ,I have not installed yet, i have prepared my disk


> If you want to boot from USB stick, your best course of action would be to install TO a USB stick 
how can i do it ?
i watched carefull the install wizard and it doesn't allow to install the grub on the usb stick

---

### Post by Vladlenin5000 on 2014-10-24
> **ramas2 said:**
> i watched carefull the install wizard and it doesn't allow to install the grub on the usb stick

There are other ways to do it albeit more complex. It was suggested to remove other drives while installing to a pendrive and that alone prevents the GRUB to be installed on anything else than the drive where Ubuntu is being installed to.

---

### Post by ramas2 on 2014-10-24
> **Vladlenin5000 said:**
> There are other ways to do it albeit more complex. It was suggested to remove other drives while installing to a pendrive and that alone prevents the GRUB to be installed on anything else than the drive where Ubuntu is being installed to.

yes i got it
but let say i'm starting to install ubuntu on my drive,steps by steps ,on the final step it asked me to select where store the grub,what should do now with my machine running ,disconnect my drive?

---

### Post by yancek on 2014-10-24
You would install Grub to the master boot record of the usb on which you are installing Ubuntu.  You should have an option in the install window, Device for bootloader installation.  The default is /dev/sda.  Not knowing what drive(s) you have attached or what they are labelled as, it's impossible to tell you.  If you are installing from a DVD and have only the usb attached, that would be where you install it.

---

### Post by ubfan1 on 2014-10-24
I use a USB with an ext2 filesystem (FAT would work too) with a boot directory.  Then identify that USB as your location for the bootloader.  Now, that should write grub to the MBR and the grub files to /boot/grub.  You need to check the device assignments in the /boot/grub/grub.cfg file, the installer probably got them all mixed up with a USB live media, USB bootloader , and hard disk .  Usually hd0/sda will be the boot USB, but I have a machine where that is usually the hard disk, so you may need to experiment.  you can edit the grub boot commands at the grub menu (Type "e", instructions at bottom of screen).  When you find the numbering which works, you may make those changes permanent by editing the /boot/grub/grub.cfg file.

---

