---
title: "Just upgraded to 15.10 epson V500 scanner not recognised"
date: 2016-04-09
forum: Installation &amp; Upgrades
---

### Post by Vic_Paine on 2016-04-09
As title, loaded Xsane but it said "no devices available" any ideas please?  
PS impressed that it picked up my MG 7550 WiFi printer straight away

---

### Post by Unterseeboot_234 on 2016-04-09
I just went through this with my HP all-in-one printer that originally worked and then went offline after an electrical interruption. What worked for me was I made sure the printer linked over a wireless network first, then I fired up Simple Scan. That got me "No Scanner Detected". Running

[FONT=courier new]sudo sane-find-scanner[/FONT]

in the terminal immediately fixed my scanner. Other factors include if you have CUPS as a printer server and/or vendor drivers installed from the vendor. Try the terminal command first.

---

### Post by Vic_Paine on 2016-04-09
Tried that with this result:
> # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0130 [EPSON Scanner]) at libusb:003:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

Seems to see it but still won't connect.  It says to read docs that came with the program but I'm afraid I have no idea where the manual would be.

---

### Post by Vic_Paine on 2016-04-09
Just checked on the sane backend page and it's not supported, is there another scanner program that will work with my scanner?

---

### Post by Vic_Paine on 2016-04-09
Tried downloading/installing drivers from the epson site.  Seemed to install OK but Xsane and simple scan still don't see it.

---

### Post by Vic_Paine on 2016-04-10
No ideas please?

---

