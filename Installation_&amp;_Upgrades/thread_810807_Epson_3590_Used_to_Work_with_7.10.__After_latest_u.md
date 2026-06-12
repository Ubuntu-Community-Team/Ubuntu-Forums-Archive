---
title: "Epson 3590 Used to Work with 7.10.  After latest updates, does not!!!"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by makoto149 on 2008-05-28
In an effort to keep my system up to date, I installed the latest updates (you know, by clicking on the annoying little asterisk at the top of the screen?).  Now my Epson 3590 Perfection scanner won't work.

I get a message saying "Failed to open `snapscan:libusb:xxx:xxx' " where xxx:xxx varies.

Running sane-find-scanner gives me:

found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:003:006

What's the deal?  Is there a way to back out of the upgrades?  I'm kind of ticked off, to be honest.  I just want my scanner to work the way it did before the "updates".  I'm almost considering doing a restore from backup from the day before I made the (in hindsight TERRIBLE) decision to install the updates.

Almost any help is appreciated.  Thanks.

---

### Post by Wilhelm Ernaus on 2008-05-31
**I have this exact same problem with the Epson 3490 Photo, it used to work and after upgrade it broke**

>>sudo sane-find-scanner -q
found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:005:008

>>scanimage -L
device `snapscan:libusb:005:008' is a EPSON EPSON Scanner flatbed scanner

>>scanimage 
[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
scanimage: open of device snapscan:libusb:005:008 failed: Invalid argument

[B]The directory listed doesn't even exist
[/B]
>>locate snapscan.conf
/etc/sane.d/snapscan.conf

>>cat /etc/sane.d/snapscan.conf | head 
#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/your-firmwarefile.bin

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

[B]Does anyone know where I find the firmware file? Is that even the problem?

Other posts seemed to indicate that you needed to be part of the scanner group? How do you find out if your part of this group?
[/B]

---

### Post by kiev on 2008-07-08
HEEEELLPPP!!!!!!
Ubuntu 8.04 amd_64 NOT WORK!!!!!

---

