---
title: "Install of usb.h on 2.6.24-17-generic ubuntu 8.04"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by Blindulo on 2008-06-17
Hi Forum.

I'm trying to install an epson DX7400 scanner/printer/copier.

Epson's page is down and I have tried 3 threads from the forum already.

I'm at using the printerdriver from the CX4400 with sucess however the scanner is still troubling me some.

sane-backend keeps saying that I need usb.h to get usb support (even if the device is found by sane-find-scanner)

Now which package contains the header file I'm looking for?

I've already tried; 
```

sudo aptitude install libusb-dev
sudo apt-get install libusb
sudo apt-get install libusb-dev

```
however I seem not to have the right source as it in the cases where I understand the result says:
```

Package libusb-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libusb-dev has no installation candidate

```
Please help - Many thanks in advance.

Blindulo


Help checked in on me - By not getting the backend from the sources the forum adviced on search of epson DX7400 but installing the extra backends from System->Administration->Synapsis Package manager->Sane extra backends it now works just fine.

---

