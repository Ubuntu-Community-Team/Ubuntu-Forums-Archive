---
title: "Problems with Dual Boot"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by pieaholicx on 2007-12-08
Okay, so I'm trying to setup a dual boot system with Ubuntu and Windows XP, but it's having problems booting XP. I've got XP on a second hard drive, and when I make that first/only drive, it boots fine, however when I try to chainload from grub I just get a message (I think it was something like "Starting..."), and then it just doesn't do anything.

From my menu.lst:
title		Windows NT/2000/XP (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

My boot.ini:
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

---

### Post by Nebutron on 2007-12-08
Are you using a raid config?  I had no problems setting up a dual boot on the same drive, but don't know if a dual boot config will work on two separate drives.

---

### Post by pieaholicx on 2007-12-08
No, I'm not using RAID. It's just two IDE drives hooked up on one chain. I can't see any reason why GRUB wouldn't be able to boot over two drives.

---

### Post by rsambuca on 2007-12-08
Windows definitely likes to be on the primary drive.  I would suggest putting the Windows drive as the primary, and the Ubuntu drive as the slave.  Then just re-install the grub loader using a liveCD.

---

### Post by pieaholicx on 2007-12-08
Okay, to make sure I get the process right:

Edit boot.ini
Shutdown
Switch Windows drive to primary
Boot off Ubuntu live cd
Run grub-install to the MBR of the Windows drive

That everything I have to do?

---

### Post by rsambuca on 2007-12-08
Why are you editing the boot.ini?  You should never have to touch it (unless you already have, for some reason).  Also, make sure your drives are jumpered correctly, and in the correct order in the bios.

---

### Post by pieaholicx on 2007-12-08
My Windows drive was originally a primary, and my (currently)Ubuntu drive was a data drive, so I had modified my boot.ini to point to the second drive. I have a copy of the original so I'll just overwrite the new one.

My drives are jumpered for auto so I should be good there. I'm not sure if my BIOS has settings for hard drive order, but if you happen to know where they are on the HP d530 CMT BIOS I can check them.

Anything I should backup from my Windows drive just in case?

---

