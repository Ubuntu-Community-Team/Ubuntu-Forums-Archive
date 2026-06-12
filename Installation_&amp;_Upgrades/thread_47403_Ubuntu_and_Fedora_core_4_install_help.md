---
title: "Ubuntu and Fedora core 4 install help"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by tesseract85 on 2005-07-08
I have installed Ubuntu linux and I would like to install Fedora Core 4; however, when I proceed to install It does not recognize that Ubuntu is there. Should I use Ubuntu's boot loader or use FC4's? 

How can I get this to work?

 What will I need to edit?

 What process should I go through?

 I am willing to reinstall. 

Where is a good place to get all the drivers for my hardware?

Thank you so muchfor the help.


Here is a list of my hardwarethat I would like someone to tell me where to get some of these drivers:

Biostar m7ncd nforce 2 chipset
dual 40gb hdd
ati radeon 9250 256mb 
creative labs audigy 2 value
motorola wpci810g

Thanks again

JR

---

### Post by mingus on 2005-07-08
Whether you want to use Ubuntu's grub or Fedora's grub to boot is a matter of choice.  Either one should work, but you need to understand *how* the process works or one will trip up the other.  Search the forums, there are a number of posts - some recent - about multi-booting Ubuntu with Fedora.

Having said that, this may be easiest:  Boot into Ubuntu.  Get into a terminal and do:
$sudo update-grub
this will hopefully find Fedora and add it to the Ubuntu grub menu
$cd /boot/grub
$cat menu.lst
look for a stanza for Fedora.  If it is there, reboot and that should do it.

---

### Post by mingus on 2005-07-08
[QUOTE=tesseract85]
Where is a good place to get all the drivers for my hardware?
[/QUOTE]

As far as the drivers, most should be found by the installation.  For example, your nforce2 chipset was found or you wouldn't be running.  Do:
$lspci
to see the devices on the PCI bus that were found by the kernel; do:
$lsmod | more
to see the driver modules being set up by the kernel

If you're lucky you won't need to do anything.  If audio, video, networking, etc. are not working, you need to post a specific question about that.

---

