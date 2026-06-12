---
title: "Ubuntu don't mount my ipod"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by romaluca on 2007-04-02
Yesterday i have remove my ipod not corretly and now ubuntu not mount it.

I try to mount it with windows and it works.

How can i do for ubuntu?

---

### Post by 1/0 on 2007-04-02
I think we need some more info to help you out there. Messages, dmesg, lsusb, manual mount, charged, charging, programs, etc. Is it similar messages to the other posts on the forum?

---

### Post by romaluca on 2007-04-02
I have the other posts but they are for ipod 2st generation. I have and ipod video 5st

and until yesterday the automatic mount worked correctly.

---

### Post by 1/0 on 2007-04-02
OK, I don't have an Ipod but I've got USB mounted stuff, s.a. printer, mouse and scanner, so I'll try to help the best I can. So tell me:

[LIST]
[*]What messages do you get when mounting the Ipod? 
[*]How do you mount it/a program? 
[*]Can you manually mount the drive? 
[*]If you plug it in do you get any messages in dmesg (command: dmesg |tail)? 
[*]What does lsusb say when the Ipod is plugged in?
[*]Is the Ipod charged?
[*]Does the Ipod charge when connected?
[/LIST]

---

### Post by romaluca on 2007-04-02
What messages do you get when mounting the Ipod?

If i insert the connetor of ipod ubuntu tell me nothing. 
But in nautilus at the address: computer:///

Is there "Apple iPod Music Player" but isn't mount.
If i click on mount happen nothing.

How do you mount it/a program?
I don't mount manually ipod. it mount automatically.
Like a usb pen drive.

If you plug it in do you get any messages in dmesg (command: dmesg |tail)?
[14496.156000] sdb: Write Protect is off
[14496.156000] sdb: Mode Sense: 68 00 00 08
[14496.156000] sdb: assuming drive cache: write through
[14496.156000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[14496.156000] sdb: Write Protect is off
[14496.156000] sdb: Mode Sense: 68 00 00 08
[14496.156000] sdb: assuming drive cache: write through
[14496.156000]  sdb: sdb1 sdb2
[14496.172000] sd 3:0:0:0: Attached scsi removable disk sdb
[14496.172000] sd 3:0:0:0: Attached scsi generic sg2 type 0

What does lsusb say when the Ipod is plugged in?
Bus 005 Device 004: ID 05ac:1209 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Is the Ipod charged?
Yes it is 


When i connect it , it show the text Do not disconnect.

---

### Post by romaluca on 2007-04-02
i suceed to mount manually ipod with:
 sudo mount /dev/sdb2 /media/ipod/

When i try to umount it from nautilus, nautilus tell me:
The volume 'IPOD' was probably mounted manually on the command line.
Devic to unmount is not in /media/.hal-mtab so it not mounted by hal.

How can i to mount if by hal??

---

### Post by 1/0 on 2007-04-02
Well, I just switched from Gentoo and its different in that distro but I'd say that that file is the problem. You could try to moving it and reboot.

```

sudo mv /media/.hal* ~/

```

If there's a problem just put it back.

---

### Post by romaluca on 2007-04-02
i have try it but the problem there is stll

---

### Post by 1/0 on 2007-04-02
As far as I know, you can't unmount the drive from Nautilus if you mounted it manually. You'll have to unmount it manually with the command "umount". 

Did you try automounting it after moving the file and rebooting or manually mounting it. At least you can mount it manually, which means that a lot of other stuff are OK, s.a. hotplug.

---

