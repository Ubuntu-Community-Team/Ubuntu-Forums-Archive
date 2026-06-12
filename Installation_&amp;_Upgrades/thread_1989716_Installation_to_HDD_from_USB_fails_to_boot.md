---
title: "Installation to HDD from USB fails to boot"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by Malfordx on 2012-05-28
I have been a windows user and when my HDD failed I ran Ubuntu 12.04 from a USB drive. I was very impressed so when my new solid state HDD arrived I decided to install Ubuntu. While logged into Ubuntu running from the USB I selected the opion from the desktop/task bar to install Ubuntu. All seemed to go well until the installation completed and I was asked to restart the machine which I duly did. When booting from the HDD the boot process only gets as far as a flashing _ in the top left corner of the screen and stays there. If I boot from the USB then all is well, however I notice that I am asked for the login password when booting from USB which is something I only set up when doing the installation on the HDD.

A bit disappointing after the seamless operation from the USB pen. my computer is a Toshiba Satellite L500, the new hard rive is a SanDisk 120GB Ultra SATA.

 Any pointers anyone can give would be helpful. I am not experienced with OS installations so could be doing something trivial wrong.

---

### Post by wilee-nilee on 2012-05-28
Hard to actually tell, as you have not figured out if you are running the usb, or the actual install.

**If you are seeing a log in this sounds like the actual install, confirm this, you should not see the install icon on the desktop to start with.**

Run this command to identify the ssd.

```
sudo fdisk -lu
```If you are in the install you can load the grub bootloader to the mbr of the ssd.

The commands are these.

Use the actual information you get from the first command for the X below, no partition numbers, just sda, or sdb, depending on what your hide drive shows in the first command above.

```
sudo grub-install /dev/sdX
```then 

```
sudo update-grub
```

---

### Post by Malfordx on 2012-05-29
Thanks Wilee-Nilee. I don't exactly understand why but that has fixed my problem :p

---

### Post by Malfordx on 2012-05-29
Is there a way to mark the thread to show that the issue has been solved? I can't find it if there is....

---

### Post by wilee-nilee on 2012-05-29
> **Malfordx said:**
> Is there a way to mark the thread to show that the issue has been solved? I can't find it if there is....

I believe it is thread tools.

You had the bootloader installed to the thumb, it happens sometimes, when a thumb is booted from. The HD, and the thumb get switched so that the thumb reads as the sda drive, normally the internal, the install defaults to loading the sda drive.

---

