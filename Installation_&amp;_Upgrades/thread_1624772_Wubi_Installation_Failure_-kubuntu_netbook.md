---
title: "Wubi Installation Failure -kubuntu netbook"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by mbsfirst on 2010-11-18
I have tried several different times to install on a Acer Netbook. This is the error message I receive
 
"Cannot download the metalink and therefore the ISO"
 
I have tried installing directly from hard drive and also via usb stick
 
Please help.

---

### Post by bcbc on 2010-11-18
the log file usually contains important info (in the %temp% folder).

but in general, this message indicates that wubi tried and failed to download a file containing the md5 hashes of the releases for the version of wubi.exe you are running. It uses this file to verify that it has found a valid CD image (.iso) file or to validate the .iso it is about to download if it didn't find a valid image. 

But if you pass on the log file (within [CODE[SIZE="1"] [/SIZE]][/CODE] tags it should be clear what the prob is.

---

