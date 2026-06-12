---
title: "Cannot Install ubuntu"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by Diana Rogger on 2008-02-25
Hi,

I bought a new computer:

Intel Core 2 Quad Q6600
CDROM SATA

When I put the cd in the rom I can select what to chose but after that the software is displaying a telling me that a cdrom can't be found.

How can I fix this problem?

Thanks

---

### Post by Pumalite on 2008-02-25
Delete

---

### Post by Diana Rogger on 2008-02-27
Can someone help me?
Does ubuntu supports SATA divices?
If I am installing ubuntu the software cannot see the cdrom because the drivers are not present I think.

How can I install ubuntu?

---

### Post by dstew on 2008-02-27
Try the kernel parameter **hda=cdrom** to inform the kernel that the hda device on your SATA connection is really a cdrom drive, not a hard drive. You might have to try hdb or hdc also. Enter kernel parameters by pressing F6 at the first menu.

---

### Post by Diana Rogger on 2008-03-05
I try but no results.

I pressed F6 ( when I am on : Install to the hard drive)
Below I can read: Boot Options z ramdisk_size=16384 root=/dev/ram rw quiet --|

After the above line I enter hda=cdrom but it failed to install
After that I tried hdb=cdrom 
I am getting the message: "Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again.

Maybe I am doing something wrong.

Any suggestion please?

Regards,

Diana

---

### Post by Pumalite on 2008-03-05
Set your BIOS to default values, or set CD to 'Advanced Support' or 'Auto'

---

### Post by Diana Rogger on 2008-03-05
I already put it the Auto.
I think ubuntu does not have the drivers for the cdrom.
The configuration is to advanced.
If I put the cd in another computer it is working

Maybe ubuntu does not supports SATA cdroms. The system is asking for a floppy with the cdrom drivers.

Does ubuntu supports SATA CDrom drives?

Motherboard is : ASUS P5E-VM HDMI

---

### Post by logos34 on 2008-03-05
If all else fails to get it to recognize the cdrom drive you could always use the [UNetbootin or CD image (.iso) method]("https://wiki.ubuntu.com/Installation/FromWindows") (no cdrom needed)

---

### Post by jimv on 2008-03-05
If you have a thumbdrive, you can install from that too.

[http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive](http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive)

---

### Post by Diana Rogger on 2008-03-06
Hi guys,

Thank you for your help.

In the mean while I installed Xubuntu and I had no problems.

The version that I wanted to install is Ubuntu server version.
Now I installed Xubuntu on a server (webserver)

Question:

1) Can I use Xubuntu also to setup a webserver?

Thank you in advanced

---

