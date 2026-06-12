---
title: "Installing Ubuntu on Win 10 system?"
date: 2016-09-27
forum: Installation &amp; Upgrades
---

### Post by gerrycassidy on 2016-09-27
Hi, 
    I have Window 10 and I would like to dual boot it with Ubuntu.  Here lies the problem.

 I would like to have Ubuntu on an external drive 1 Terabyte, independant of Windows 10. 
 
Is it possible to only have the grub on Windows 10.
 
thankyou for reading my post.

Gerry

---

### Post by yancek on 2016-09-27
If you have a pre-installed instance of windows 10, it is likely using UEFI so you would need Ubuntu installed UEFI.  The best source of information on this is at the Ubuntu documentation site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by yetimon_64 on 2016-09-27
> **gerrycassidy said:**
> Hi, 
    I have Window 10 and I would like to dual boot it with Ubuntu.  Here lies the problem.

 I would like to have Ubuntu on an external drive 1 Terabyte, independant of Windows 10. 
 
Is it possible to only have the grub on Windows 10.
 
thankyou for reading my post.

Gerry

Grub installs its files to the /boot/grub folder on Linux (Ubuntu). So for grub supplied by the linux install, no you can't put it on the Windows 10 install; unless you download and install something like "[[COLOR=#0000ff]grub2win[/COLOR]]("https://sourceforge.net/projects/grub2win/")" (sourceforge link) instead which holds its files in Windows.

Though another option would be to leave the Windows 10 installation alone altogether and install (normal linux) grub to the external drive as part of a full installation of ubuntu to the external drive. 

Then using the UEFI menu select which hard drive you want to boot. You can then either boot directly into windows without interference by any other non windows bootloader (grub in this case) or if you choose the external drive you can get a grub boot screen (wholly installed on the external drive) from which you can boot either into Ubuntu or Windows (grub will also find the Windows install and put an entry in for it as well).

I would recommend sticking normal grub on the external drive; if you unplug the external drive you will then still have full normal access to Windows without a possibly damaged bootloader set up in the way.

I don't have a windows installation any more but actually use the above idea of installing a separate system with its own grub menu on a 500 GB external drive here. I have a normal full GUI multiple release ubuntu dual boot set up on this laptop and a headless "tool set" installation of ubuntu on partitions on the back end of the external drive. The external drive has its own fully set up grub boot screen with the boot loader installed to the external drive. I can select either hard drive from the UEFI boot menu and go to its own different bootloader screen. In your case the Windows installation and bootloader could remain totally untouched if you keep all the ubuntu installation and boot loader on the external drive and select which hard drive you want to boot through the UEFI menu.

Regards, yeti.

Edit: particularly note the UEFI link yanceck posted above, it is important info to know about when using with Win 10.

---

