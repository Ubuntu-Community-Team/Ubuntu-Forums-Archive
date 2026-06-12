---
title: "Espon printer not detected as a usb device"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by dogdo on 2010-01-11
Hi

I have a Epson Stylus SX115 All In One Printer which i connected to ubuntu 9.10 the other day. Upon installation the drivers for the stylus SX 115 were not available, but there were drivers for the stylus SX110 which i then installed. Printing is fine although for some reason even though i connect via usb cable the printer is not detected as a external device. I have to pull out the usb cable without unmounting-what should i do?
[COLOR=#888888]
[/COLOR]

---

### Post by SecretCode on 2010-01-11
Is it listed in *lsusb*?

I'm guessing that because it's not a disk device it doesn't need safe removal.

---

### Post by dogdo on 2010-01-11
> **SecretCode said:**
> Is it listed in *lsusb*?

I'm guessing that because it's not a disk device it doesn't need safe removal.

Is lsusb a sudo command? But the printer connects via usb -should it not have to be mounted/unmounted?

---

### Post by SecretCode on 2010-01-12
lsusb is a terminal command but it doesn't need sudo. Run it and post the results.

"Mounting" means attaching a filesystem found on a device to a particular directory (mount point) in your directory structure. You can't really "mount" other kinds of device.

And the reason "unmounting" matters is that some writes to a disk are cached and not written immediately. Unmount, eject, safely remove etc make sure those caches are fully written.

I don't see how any of this applies to a printer. The worst that can happen if you pull the plug is that you lose a print job - you would never leave the printer in an inconsistent state where it can't be used again.

So I don't think you have anything to worry about. :)

---

### Post by dogdo on 2010-01-12
Ok here is lsusb on my pc without any any devices attached via usb:

shinji@shinji-laptop:~$ lsusb
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c251 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

And here is lsusb with the printer attached:

shinji@shinji-laptop:~$ shinji@shinji-laptop:~$ lsusb
shinji@shinji-laptop:~$: command not found
shinji@shinji-laptop:~$ Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
shinji@shinji-laptop:~$ Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
shinji@shinji-laptop:~$ Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
shinji@shinji-laptop:~$ Bus 004 Device 002: ID 046d:c251 Logitech, Inc. 
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
shinji@shinji-laptop:~$ Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
shinji@shinji-laptop:~$ Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
shinji@shinji-laptop:~$ Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
shinji@shinji-laptop:~$ Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
shinji@shinji-laptop:~$ Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found

Oh god...what is going on? what are all these errors?

---

### Post by SecretCode on 2010-01-12
:D It looks like you pasted the output of the previous command in, instead of typing lsusb again!

Attach the printer and type *lsusb* at the command line

---

### Post by dogdo on 2010-01-12
Ok this is what i got from running that sudo command once with the printer:

shinji@shinji-laptop:~$ lsusb
Bus 004 Device 002: ID 046d:c251 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04b8:084d Seiko Epson Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
shinji@shinji-laptop:~$

---

### Post by SecretCode on 2010-01-12
> **dogdo said:**
> 
Bus 005 Device 002: ID 04b8:084d Seiko Epson Corp. 


So your Epson is detected as a usb device!

> **SecretCode said:**
> So I don't think you have anything to worry about. :)

---

### Post by dogdo on 2010-01-12
Ok so my printer does not have a file system on it-therefore not mounting/unmounting will not damage the printer or pc. 

You''ll have to forgive my slowness..have been using windows for years so the idea of not 'safely removing a device' is so new to me.

---

