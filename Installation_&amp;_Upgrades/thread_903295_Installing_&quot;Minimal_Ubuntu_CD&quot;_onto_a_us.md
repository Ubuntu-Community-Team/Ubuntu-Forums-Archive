---
title: "Installing &quot;Minimal Ubuntu CD&quot; onto a usbpen???"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by LeeDavies on 2008-08-28
Hello Everyone,

I've installed full blown Ubuntu 8.04 (persistent) onto a usbpen following the instructions on pendrivelinux.com. 

What I really need is a minimal graphical installation with IceWM or Fluxbox.

Does anyone know if there is a way of installing the "Minimal Ubuntu CD" (persistent) onto a USB?

Regards,

Lee

---

### Post by az on 2008-08-28
> **LeeDavies said:**
> Hello Everyone,

I've installed full blown Ubuntu 8.04 (persistent) onto a usbpen following the instructions on pendrivelinux.com. 

What I really need is a minimal graphical installation with IceWM or Fluxbox.

Does anyone know if there is a way of installing the "Minimal Ubuntu CD" (persistent) onto a USB?

Regards,

Lee
Create a small fat16 partition for the live image.  Create another partition with an ext3 filesystem labelled "casper-rw"

Copy all the contents of the iso image onto the small partition.  Move the contents of the casper folder down to the root.  Rename isolinux.cfg to syslinux.cfg.  Edit the file to add the work "persistent" after casper (Ex: "boot=casper persistent") - Do that for at least the default entry.

Install syslinux and run

sudo syslinux /dev/sdc1 (or whatever the partition is that has the live cd on it.)

Next, boot the device.  That's all.


[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

[http://ubuntu-rescue-remix.org/node/21](http://ubuntu-rescue-remix.org/node/21)

You can create your own custom live cd, too:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by LeeDavies on 2008-08-28
> Move the contents of the casper folder down to the root. 

Mmmm... I maybe looking at the wrong thing but the "Ubuntu 8.04 Minimal CD" doesn't have a casper folder?

---

### Post by Pumalite on 2008-08-28
Maybe these links will help:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)
[http://ubuntuforums.org/showthread.php?t=611763&page=2](http://ubuntuforums.org/showthread.php?t=611763&page=2)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

---

### Post by LeeDavies on 2008-08-28
> maybe these links will help:
[https://help.ubuntu.com/community/In...wMemorySystems](https://help.ubuntu.com/community/In...wMemorySystems)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.debuntu.org/how-to-instal...nux-on-usb-bar](http://www.debuntu.org/how-to-instal...nux-on-usb-bar)
[http://ubuntuforums.org/showthread.php?t=611763&page=2](http://ubuntuforums.org/showthread.php?t=611763&page=2)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://www.pendrivelinux.com/2007/09...ibbon-install/](http://www.pendrivelinux.com/2007/09...ibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.pendrivelinux.com/2008/04...-from-windows/](http://www.pendrivelinux.com/2008/04...-from-windows/)
[http://www.pendrivelinux.com/2008/04...drive-install/](http://www.pendrivelinux.com/2008/04...drive-install/)

Thanks for the feedback. 

I've already been visited most of these links (pendrivelinux.com is a great site). 

There are links to installing minimial Ubuntu and links for install Ubuntu on usbpens but no links for installing a minimal Ubuntu on a usbpen :(

---

### Post by az on 2008-08-28
> **LeeDavies said:**
> Mmmm... I maybe looking at the wrong thing but the "Ubuntu 8.04 Minimal CD" doesn't have a casper folder?

I thought you meant a custom minimal cd.

The Ubuntu minimal CD does not run a live system like the desktop cd.  It runs the alternate installer.  It downloads the packages for the base system from the net.  You cannot run a persistent system from it.

---

### Post by LeeDavies on 2008-08-28
> The Ubuntu minimal CD does not run a live system like the desktop cd. It runs the alternate installer. It downloads the packages for the base system from the net. You cannot run a persistent system from it.

Ah, it downloads the packages. I was hoping it was a small "complete" installation, which I could copy the relevant bits from onto a usbpen.

It looks like the best solution is in one of the sites you suggested -

[https://help.ubuntu.com/community/Li...ionFromScratch](https://help.ubuntu.com/community/Li...ionFromScratch)

It details how to build your own Ubuntu distro from scratch and how to install it onto a usbpen.

Many thanks to you all.

Lee

---

### Post by snowpine on 2008-08-28
Hi Lee, as others have pointed out, the Ubuntu Minimal is not the right choice for you because it's only an installer. :)

I find that Crunchbang is a very nice Ubuntu-derived pen drive distro because it requires less disk space, uses the Openbox windows manager, and has lots and lots of useful applications. If you are looking for something teeny-tiny, SliTaz is about 25mb, it is really amazing. (But it is not based on Ubuntu so you will have a steep learning curve.)

---

### Post by Sorivenul on 2008-08-28
Perhaps Minibuntu may be for you:
[http://minibuntu.crealabs.it/]("http://minibuntu.crealabs.it/")

From there following az's directions should work, I think.

---

