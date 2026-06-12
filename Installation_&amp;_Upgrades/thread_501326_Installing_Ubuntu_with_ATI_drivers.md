---
title: "Installing Ubuntu with ATI drivers"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by gecko on 2007-07-15
This was used to install Ubuntu with ATI drivers when the install GUI (GDM) failed to start. We were unable to access networking for similar reasons and so could not access Ubuntu packages. 

Download the latest ATI Linux x86 driver from the website. Save it to a USB stick as it is over 50MB. Start the Ubuntu installation process and when GDM fails to start then do the following.

Plug in the USB stick with the ATI drivers. You should see a message on the screen "sdb: assuming drive cache:..." . The text "sdb" is what you need. That is the device name. Your device name may be different so use what you have. The full device name is /dev/sdb and we need to access the first partition on the USB stick which is referred to as /dev/sdb1. Use the following commands to access the USB drive.  Replace the device name with what you have. If your device is sdb then the commands would be as follows.

sudo mkdir /mnt/usbflash
sudo mount /dev/sdb1 /mnt/usbflash
ls /mnt/usbflash

You should now see a list of files from the USB drive. You need to copy the ati drivers to system with the following commands. 

cd /tmp
cp /mnt/usbflash/ati*  .      (thats a star, followed by a space, then a dot)
sudo ./ati*

Follow the defaults the driver will install itself. When it is nearly finished it will ask you if you want to start a web browser however don't do this. Now we have to configure X11 to use the new driver.

sudo aticonfig --initial --input=/etc/X11/xorg.conf

Now we should be able to start gdm and continue the install process. Use the following command to start the X11 server. 

sudo gdm

On the desktop you will see an install Icon. Use this to continue installing Ubuntu. 

When the system first reboots after finishing its installation it will fail to bring up the graphical user interface (GUI). The installation files from the CD do not contain the ATI drivers so the installed system does not have them. Follow the same steps as shown above except for the last (sudo gdm) command above.  Use the command below to reboot the system.

sudo reboot.

When the system reboots the GUI should start as normal.

I hope this helps all those people who wanted the promise of Ubuntu and the installation failed them.

Regards

Kevin

---

