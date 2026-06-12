---
title: "USB Filmscanner - anyone yet got one running in Karmic or prior?"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-19
Bus 001 Device 005: ID 05a9:1550 OmniVision Technologies, Inc. VEHO Filmscanner.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Also known as "Vupoint FS-C1-VP", "*VEHO* VFS-001", ans some more generic, this one is just called "Filmscanner".

Main vendors are  here:
[http://www.vupointsolutions.com/FS-C1-VP.asp](http://www.vupointsolutions.com/FS-C1-VP.asp)
[http://www.veho-uk.com/productdetail.aspx?id=31](http://www.veho-uk.com/productdetail.aspx?id=31)
I am almost sure it uses this sensor: 
[http://www.ovt.com/products/ip_detail.php?id=7](http://www.ovt.com/products/ip_detail.php?id=7)

Haven't seen a "yes" or "no" anywhere, and have seen an "almost certain" that it would work with VueScan Scanning Software:
[http://www.hamrick.com/](http://www.hamrick.com/)

But alas, not detected, nor in GIMP, nor inXszne, or IrfanView in WINE, or SANE.
As for the Win Drivers and software, they use ArcSoft Photoimpression and WINE says "no".
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17837](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17837)
Supplied Photomipression is  Version 6.) and there is a 6.5 available:
[http://www.arcsoft.com/estore/software_title.asp?ProductCode=PI65](http://www.arcsoft.com/estore/software_title.asp?ProductCode=PI65)

Comments, hints, links, suggestions welcome!

---

### Post by Woody1987 on 2009-10-19
try it in vlc

---

### Post by rogerdean on 2009-10-19
I've got a Plustek OpticFilm 7200 scanner, and try to get it working once a year or so. No drivers, I understand... 

But I've just tried to install the XP driver under wine, and that seemed to go ok. We'll see when i get home and connect up

Woody, can you elaborate? VLC is for videos, no? 

Cheers

---

### Post by cariboo on 2009-10-19
Just out of curiosity, what is the output of:

```
dmesg | tail -n15
```

when you plug the device in?

---

### Post by lborkey on 2009-10-20
Here's what I see (in Jaunty):

[1548934.556533] usb 1-6: new high speed USB device using ehci_hcd and address 5
[1548934.689857] usb 1-6: configuration #1 chosen from 1 choice
[1549059.880551] usb 1-6: USB disconnect, address 5
[1549129.616034] usb 1-6: new high speed USB device using ehci_hcd and address 6
[1549129.749837] usb 1-6: configuration #1 chosen from 1 choice
[1549140.751264] usb 1-6: USB disconnect, address 6
[1549146.448034] usb 1-6: new high speed USB device using ehci_hcd and address 7
[1549146.581863] usb 1-6: configuration #1 chosen from 1 choice
[1549315.467626] usb 1-6: USB disconnect, address 7

---

### Post by emarkay on 2009-10-20
I don't see any USB or Flatbed Scan input options for VLC.

Also:id

uid=1000(username) gid=1000(username) groups=4(adm),20(dialout),24(cdrom),29(audio),46(plugdev),103(fuse),
104(lpadmin),112(netdev),115(admin),122(sambashare),1000(username)

And: sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.
  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
found USB scanner (vendor=0x05a9, product=0x1550) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
  # Not checking for parallel port scanners.
  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

And:  dmesg | tail -n15

[   31.608364] CPU1 attaching sched-domain:
[   31.608367]  domain 0: span 0-1 level MC
[   31.608371]   groups: 1 0
[   31.608376]   domain 1: span 0-1 level CPU
[   31.608379]    groups: 0-1 (__cpu_power = 2048)
[   35.570200] CPU0 attaching NULL sched-domain.
[   35.570212] CPU1 attaching NULL sched-domain.
[   35.588149] CPU0 attaching sched-domain:
[   35.588156]  domain 0: span 0-1 level CPU
[   35.588161]   groups: 0 1
[   35.588171] CPU1 attaching sched-domain:
[   35.588174]  domain 0: span 0-1 level CPU
[   35.588178]   groups: 1 0
[ 2196.620276] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 2196.754190] usb 1-3: configuration #1 chosen from 1 choice

Thanks all, any other ideas?

---

### Post by emarkay on 2009-10-20
FWIW, confirmed it works in Windows.

---

### Post by emarkay on 2009-10-21
Regarding VueScan program, respomse from Tech Support:

"Unfortunately, VueScan doesn't work with this scanner.  I think 
it's actually a video camera, so you might try some video camera 
drivers to see if they work."

Yes it is a "movie" camera in that as you insert slides, you see that motion.  I will look and see if there are any appropriate "webcam" drivers out there.

---

