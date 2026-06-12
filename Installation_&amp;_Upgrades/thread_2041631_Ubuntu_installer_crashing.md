---
title: "Ubuntu installer crashing"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by DSJ479 on 2012-08-13
Im trying to install ubuntu 12.04 LTS on my desktop (Dell E521)
I ran DBAN before this and i think it might have something to do with it. When i go to install Ubuntu i get a error saying

"The following file does not match its source copy on the CD/DVD:

/target/lib/firmware/ar9170-1.fw

This is often due to a faulty CD/DVD disk or Drive. or a fualty hard disk.

If i skip it, this error comes up...

The installer encountered an error copying files to the hard disk

[Errno 5] Input/output error



I have tried using a CD and a USB stick to intstall it and i get the same thing every time...

---

### Post by lindsay7 on 2012-08-13
What all is on this drive at this time?

---

### Post by DSJ479 on 2012-08-13
The drive is blank

---

### Post by lindsay7 on 2012-08-13
I would try using the Live Ubuntu cd or usb to start up the computer and then use Gparted to format and set up your partition table. You could just format it if you want and them set up your partitions when you run the install Ubuntu from the live usb or live cd.

---

### Post by 2F4U on 2012-08-13
> **DSJ479 said:**
> Im trying to install ubuntu 12.04 LTS on my desktop (Dell E521)
I ran DBAN before this and i think it might have something to do with it. When i go to install Ubuntu i get a error saying

"The following file does not match its source copy on the CD/DVD:

/target/lib/firmware/ar9170-1.fw

This is often due to a faulty CD/DVD disk or Drive. or a fualty hard disk.

If i skip it, this error comes up...

The installer encountered an error copying files to the hard disk

[Errno 5] Input/output error



I have tried using a CD and a USB stick to intstall it and i get the same thing every time...

Am I right in assuming that you verified the checksum of the downloaded iso file before burning it to cd or usb?

---

