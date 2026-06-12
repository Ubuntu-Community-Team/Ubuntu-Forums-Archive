---
title: "Boot Ubuntu 8.04 from Grub on a Usb Stick"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by MrGreen on 2008-05-20
Hi,

I am trying to get Ubuntu 8.04 [iso] to boot from a usb stick, most of the guides [wiki included!] use syslinux which for me does not work. Managed to get grub onto usb drive but am having problems setting up menu.lst

Ubuntu finds vmlinuz and initrd.gz but then boots my laptop as normal ;-(

device.map

```
(hd0) /dev/sda
``` 

menu.lst

```
root 	(hd0,0)
kernel /casper/vmlinuz root=/dev/sda1
initrd /casper/initrd.gz

```

I have a feeling I need just a little more to get this work, any ideas?

MrG

---

### Post by dstew on 2008-05-20
I am not sure exactly what you are trying to do. Can you tell me what guide you are using? Broadly, there are two Ubuntu-on-a-stick projects that require booting. One is creating a stick that behaves like a Live CD, to use to install Ubuntu onto a hard drive. The other is installing a "persistent" Ubuntu system on a USB stick, to act as a full Ubuntu system including using the USB as it's "hard drive". One is called "Installing *from* a USB stick", the other is "Installing *to* a USB stick".

The menu.lst output is the kind that is used to do the first thing, that is, to make a USB stick that behaves like a Live CD. It is not a persistent system.

---

### Post by MrGreen on 2008-05-20
I would like to run persistent version 

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

But this uses syslinux, It does work ok it boots but I do not get syslinux menu at all [would not boot at all on my laptop!]

So I thought I would install grub to usb stick instead 

Of course my menu.lst is not working correctly at the moment as it booted my laptops own ubuntu install

I have read many different guides some on grub some on ubuntu, trying to combine the two

MrG

---

### Post by dstew on 2008-05-20
I read a little more. Making a persistent installation is a kind of hack on the Live CD environment. When it is finished, the USB stick contains a modified Live CD system that allows the use of the RAM file system plus a partition that stores programs on the USB stick.

You can use grub to boot a USB stick, but it is more difficult to install than syslinux, and you might have more trouble when you put the stick in another computer because of the way grub addresses disks. See [this page.]("http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=45")

Also, [this site]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/") seems to have some special help to create the persistent USB Hardy system.

---

### Post by MrGreen on 2008-05-20
I may give syslinux another go, only menu did not come up last time I tried it unless there is a special way to invoke it.

As article says grub is easier but large, syslinux version I tried would not boot on my laptop where as grub would [confused!]

Would like to carry iso on a stick much smaller, more portable even if it did not boot on another system there is always wubi :-)

Thanks for your help

MrG

---

### Post by JohnGalt131 on 2008-09-02
I use a persistent USB Xubuntu 7.10 with GRUB.  It is a 'rescue disk' of sorts... I would never carry a live CD With me everywhere, while this inconspicuously hangs from my key-chain at all times. I would now like to find a tutorial for Ubuntu (Not Xubuntu) 8.04 that uses GRUB as well.  However, the only reason I'm so attached to GRUB is that on the USB Drive I also have a BARTPE install (For when I have to fix problems more exclusive to windows on my family's PCs), so, when I boot from the USB GRUB Lets me choose whether to boot Xubuntu or BARTPE. Can this be done with Syslinux? If so, I may just use one of the many Syslinux tutorials and forget GRUB (Even though I love it so).

---

