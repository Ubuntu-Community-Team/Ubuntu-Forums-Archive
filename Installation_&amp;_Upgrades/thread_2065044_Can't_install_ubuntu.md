---
title: "Can't install ubuntu"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by Champlin93 on 2012-09-30
I'm trying to do a standard install of Ubuntu 12.4.1 on my computer after accidentally using [Pen Drive Linux's USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button") on my Ubuntu partition. When trying to install i get an error saying unable to unmount /cdrom device busy. 
Upon checking Gparted i see that sda5 (what use to be SWAP space before my accident) is mounted to /cdrom and sda5 and 6(ubuntu partition) are both labeled PENDRIVE and sda5 indeed can't be unmounted.  
So i tried the command ```
sudo umount -l -r -f /cdrom
```.  No errors were given and upon checking Gparted is is indeed unmounted but i still can't format it to SWAP because the device is still "busy".  
Any suggestions?

---

### Post by Bashing-om on 2012-10-01
Champlin93; Hi ! Welcome to the forum .

How about a approach like this:
As a  forced umount "umount -f"  doesn't resolve anything . The quick fix is a lazy unmount:
```
umount -l /mnt/deadmount
```Another fix for those who do not have mount -l option is smbumount (which worked like a charm for me), I did however first kill the smbmount process manually, not sure it that was needed. -> But:
--
a better way is to learn which process uses the device
```
 umount /dev/sdb1
``` <substitute your device/partition>
umount: /dev/sdb1: device is busy  <-output of command  example
umount: /dev/sdb1: device is busy  <-output of command example
```
 fuser -m /dev/sdb1
```/dev/sdb1: 3322

3322 is id of the process in this example that uses the device. if you like to know what it is, you may try this:
```
ps aux | grep 3322
``````
 kill -9 3322
``````
 umount /dev/sdb1
```that should work.. 
--

---

