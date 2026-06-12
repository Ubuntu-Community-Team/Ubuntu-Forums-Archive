---
title: "Absolute minimal USB live install"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by salty85 on 2010-12-16
Hello,
  I am trying to setup my girlfriends old acer POS laptop with a live USB bootable ubuntu install.  I did a live USB but found it was not persistant, I have a 1 GB USB drive I would like to use.  She wants 2 things, firefox and open office (or wine to use office 2003).  Her computers hard disk controller died, so I need to make her computer usable.  USB is my only option.  The live USB that I tried of 10.10 worked great, but I need it install persistant and have it so she can just save a doc file if she needs to work on a paper.  I need to remove the extra clutter (drivers she does not use and any extras she would not need for it to work with a full gui).  She is a noobie at computers, its painful to watch how much some days :popcorn:.  Please assist on how to get this installed and working, after the initial install I don't anticipate her needing to update anything.  I currently have a VMware install of ubuntu working and updating itself so I can do the USB boot thing.  Any advice would be great!  Thanks.

---

### Post by Megaptera on 2010-12-16
This guide says 'at least' 1gb whereas most others say 2gb. Not tried this one myself but hope it's of some use to you?

"In order to reproduce this tutorial, you will need a few items such as:
a ubuntu liveCD
a usb bar of at least 1G
a running Linux operating system"

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

---

### Post by dabl on 2010-12-16
All you can do with a 1GB stick is make a "Live CD" - install the Live CD on the bootable stick, with no persistence and no other (permanent) packages.  It's better than no OS, but it's not very flexible or adaptible.

According to Ubuntu, you need a 2GB stick:  [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)  (Under #2, tick "USB Stick" and then click "Show me How")

But, if you download the Live CD ISO image, you can follow this: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) just don't try to make it persistent and it will stay in the 1GB limit.

---

### Post by K.J. on 2010-12-16
I'm not sure I see why you want it to be live? Perhaps, it might suit you to just install the OS right on the thumb drive. I highly recommend lUbuntu. It's very light and makes my cheap eee901 fly! Between lUbuntu and the real-time kernel I was able to get qSynth/Jack down to 8ms from 50ms.

---

### Post by salty85 on 2010-12-16
I know that the live USB worked with about 750 MB, and all she would need is the ability to websurf maybe, but mostly work on open office

---

### Post by dabl on 2010-12-16
This guide will work for your purpose, and you can just disregard the part about an extra data partition on the same USB stick:

[http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

So you'll partition the entire stick as a single ext2 partition, then you'll mount your Live CD ISO and also the USB stick, and you'll copy all the files out of the ISO onto the USB stick, and finally you'll install Grub on the MBR of the USB stick.

---

### Post by salty85 on 2010-12-16
If it would make it easier, I can use the GUI in ubuntu.  I have a working VMware install I am just setting up.  Can I use FAT or FAT32 as the file system?  I need to make it so she can work between windows and Unix for her files.

---

### Post by dabl on 2010-12-16
FAT32 is OK, although the only reason I know of to do that is if you want Windows to be able to read it for some reason.  I much prefer ext2 on USB sticks, because you can fsck them (you can fsck FAT32, but ... it's still FAT and not very rugged).

---

### Post by salty85 on 2010-12-16
yeah, this is for my girlfriends computer.  Her computer works for all reasons but the disc controller.  She needs to make sure papers she submits for grad work work in office 2003, thanks for the advice

---

### Post by C.S.Cameron on 2010-12-16
You will not get far with a 1GB drive.
A new 4GB drive should be less than $10.

Anything she does in Open Office as a doc should show up ok in Office 2003.

Things done in Office 2003 might not show up exact in OOO though.

---

### Post by salty85 on 2010-12-17
Perhaps would ubuntu netbook be good though it is not a netbook?

---

### Post by K.J. on 2010-12-17
> **salty85 said:**
> Perhaps would ubuntu netbook be good though it is not a netbook?

If you're looking for a very lightweight version, I highly recommend lUbuntu. I think it comes pre-loaded with Abiword and Gnumeric (which are much faster than OpenOffice, but don't have quite as many advanced features).

You can always install OpenOffice from the repositories if you'd like.

---

### Post by salty85 on 2010-12-17
I ended up caving and using my 8 GB stick for it.  As soon as I made the logon IDs (it degfaulted to live user), and rebooted... it gave me an error of no boot entry.... oyvey

---

### Post by K.J. on 2010-12-17
> **salty85 said:**
> I ended up caving and using my 8 GB stick for it.  As soon as I made the logon IDs (it degfaulted to live user), and rebooted... it gave me an error of no boot entry.... oyvey

I still think for your use, it makes much more sense to just install onto that thumb drive instead of making it an "actual" live install.

---

### Post by C.S.Cameron on 2010-12-17
> **salty85 said:**
> I ended up caving and using my 8 GB stick for it.  As soon as I made the logon IDs (it degfaulted to live user), and rebooted... it gave me an error of no boot entry.... oyvey

I think first add user in Administration/Users and Groups.
Then go to Administration/Login Screen.

8GB should be enough for a Full install.
Best to unplug your internal HDD before installing.
If that's not possible, use manual partitioning and make sure you install the bootloader to the flash drive.

---

### Post by salty85 on 2010-12-18
i thought a full install was the usb boot disk creator in ubuntu

---

