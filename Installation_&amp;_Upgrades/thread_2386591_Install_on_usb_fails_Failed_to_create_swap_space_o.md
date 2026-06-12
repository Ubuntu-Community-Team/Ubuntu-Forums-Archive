---
title: "Install on usb fails: Failed to create swap space on partition..."
date: 2018-03-07
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2018-03-07
I'm trying to install 16.04 from cdrom onto a usb stick (/dev/sdb) in a 12.04 installation on a PC. I select the option to format /dev/sdb1 and mount it as the root directory. Then it tells me that the swap partition on /dev/sda5 and /dev/sdb1 will be formatted. When it proceeds, I get a message window saying "Failed to create swap space on partition 5..." and the message window is unresponsive. The only thing I could do was power down the PC.

Could this be due to /dev/sda5  being an extended partition?

---

### Post by TheFu on 2018-03-07
So you are trying to reuse a swap from 12.04 on a new 16.04 USB install?  Is the swap active at the time?  That would be bad.

Can't really tell with the info provided.  A boot-info report would be helpful.

BTW, support for 12.04 ended almost a year ago.

---

### Post by bilkay on 2018-03-07
I'm not trying to do anything except install 16.04 on the usb. I don't know what the install is trying to do.

---

### Post by sudodus on 2018-03-07
If you are using 'Something else' at the partitioning window of the installer, you should turn off using /dev/sda5 for swap. Then you should go to the bottom of the window, and make sure that you will install the bootloader into the external drive (which should be /dev/sdb according to the info in the opening post).

See the following links and links from them for more tips,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

Things will be easier, if you can disconnect/unplug the internal drive.

---

### Post by TheFu on 2018-03-07
> **bilkay said:**
> I'm not trying to do anything except install 16.04 on the usb. I don't know what the install is trying to do.

Well, if your system is like most others, then sda is the internal HDD and sdb is the USB drive.  Any reference to sda is a problem for the installer if you want only the USB storage used, probably.

---

### Post by bilkay on 2018-03-08
> **sudodus said:**
> If you are using 'Something else' at the partitioning window of the installer, you should turn off using /dev/sda5 for swap. Then you should go to the bottom of the window, and make sure that you will install the bootloader into the external drive (which should be /dev/sdb according to the info in the opening post). ...

Thanks (to all). The installer doesn't seem to give an option to not format the swap partition, just turn it off, which is what I did on retry. It looks like it worked - very slowly.

---

