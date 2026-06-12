---
title: "install on a USB drive"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by taughannock on 2010-08-12
Trying to install Ubuntu Netbook remix 10.4 on a USB drive. My situation is I have a notebook and the main disk controller is not working but the drive does. I would like to install Ubuntu on the drive in a USB enclosure. I understand how to get this to run this like a USB pen drive but I want to do an actual install. I have had no luck with this idea.

---

### Post by snowpine on 2010-08-12
1) Boot Ubuntu Live CD or Live USB

2) Click the Install Ubuntu icon on the desktop

It is that simple. :)

However, there is one bug in the Ubuntu installer. If you understand how GRUB works, you should click on the Advanced button on the final installer screen and make sure it is installed to the correct drive. If you don't understand GRUB, your safest option is to physically disconnect all drives except for the drive you're installing to, that way there's no possibility of error.

---

### Post by oldfred on 2010-08-12
+1 on snowpine's recommendations.

A visual walk thru, That is is a USB drive should make no difference:
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

From Karmic but the same advance button is shown:
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

---

### Post by taughannock on 2010-08-12
The USB drive does not appear selectable to install to. The choices of mountable volumes to install are nada. That is the difficulty yet I can boot of this same USB drive.

---

### Post by taughannock on 2010-08-12
This reference example is using 2 hard drives - neither USB. 

As a temporary solution I made a USB to ZIF adapter and run a PATA 128GB disk with the temporary pen drive version and this seems to work. I have a 4GB pen drive with the same Ubuntu version and was hoping I could use this to install to the PATA but stil no luck getting this volume to appear in the install dialogue.

---

### Post by oldfred on 2010-08-12
If it is a full install it is not an install disk. The easiest way to make an install disk is with Startup Disk Creator in System Administration.

I like just copying the ISO to the USB drive and using grub to boot the USB drive. But you have to add loopmount entries to the grub.cfg.

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
With details on some of the caveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by oldfred on 2010-08-12
I have one USB 4GB with grub2 booting several ISOs directly and a 16GB flash drive with a full install of Ubuntu. It may depend on your system on whether you can boot USBs or not.

---

### Post by snowpine on 2010-08-12
> **taughannock said:**
> The USB drive does not appear selectable to install to. The choices of mountable volumes to install are nada. That is the difficulty yet I can boot of this same USB drive.

That is weird... perhaps try pre-partitioning the drive using Gparted prior to launching the installer?

It is possible your computer BIOS does not support this, I suppose.

---

### Post by taughannock on 2010-08-13
Thank you so much for your kind assistance. The links and GRUB suggestion were very helpful.

---

