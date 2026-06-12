---
title: "upgrade of wubi 11.04 to 12.04 crushed grub"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by byulent on 2012-06-10
I use Windows 7 along with wubi 11.04. While I was working on ubuntu I was asked if I want to upgrade to 12.04 by the system update manager. I followed the instructions and finally when I rebooted, the grub menu appeared but whatever I choose the computer prompts:

error: no such partition.
error: no such partition.
error: no such partition.

press any key to continue...

The grub menu is as follows:
    GNU GRUB version 1.99-21ubuntu3.1

Ubuntu, with Linux 3.2.0-24-generic
Ubuntu, with Linux 3.2.0-24-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)


How can I correct the grub?

Thanks in advance,
Bulent

---

### Post by wilee-nilee on 2012-06-10
Upgrading a wubi is not advised.

Grub is not the same in a wubi.

There is really only one user on the forum that can help you here, you will have to wait for them to see your thread, they are on everyday pretty much.

---

### Post by byulent on 2012-06-10
I thought since the update manager itself asks for an upgrade it would be safe. But it seems it was not.

---

### Post by Frogs Hair on 2012-06-10
Wubi upgrades _sometimes_ work. A Gnome 2 to Gnome3 upgrade can be a problem for a standard dual boot. Preforming a fresh Wubi installation may be a better idea an may be less time consuming than trying to salvage the upgrade. I hope you made backups prior to starting which is recommend for any upgrade. 

Wubi installs Ubuntu in a folder inside the Windows and not on its own partition . Wubi uses the Windows boot loader and a modified version of grub.

---

### Post by byulent on 2012-06-10
how do I save Windows then?

---

### Post by coffeecat on 2012-06-10
> **byulent said:**
> how do I save Windows then?

With wubi, the first OS choice menu you should see is the Windows one with the choice of just Windows and Ubuntu. Only after choosing Ubuntu should you see the grub menu you are describing. Do you not see the Windows boot menu first? If you do, what happens when you select Windows from this?

We need to get an overview of your system with the boot info script. Because you are unable to boot into your wubi Ubuntu, you will need to prepare an Ubuntu live CD or live USB from the ISO downloaded from here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Here is how you burn the ISO to CD or USB stick:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

You must then set the BIOS of your computer to boot from the optical drive or from a USB device, depending on what you have prepared. Boot up the live Ubuntu CD or USB, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page, but see below - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

There is an error in the instructions. After you have extracted the downloaded tar.gz file, the script is called bootinfoscript. Therefore, once you have moved the script to the live desktop, you need to run:

```
sudo bash ~/Desktop/bootinfoscript
```

... and not what is given on the linked page.

---

### Post by byulent on 2012-06-11
I do not see Windows boot menu. Grub appears first and whatever I choose the error explained in the fist post appears.

---

### Post by byulent on 2012-06-11
I restored the broken grub by using "rescatux" software. I burned a CD with rescatux image. Booted the computer with the CD and followed the instructions for installing grub.

Thanks anyway.

---

