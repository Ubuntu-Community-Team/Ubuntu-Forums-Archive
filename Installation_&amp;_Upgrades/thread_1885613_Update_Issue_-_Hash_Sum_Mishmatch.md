---
title: "Update Issue - Hash Sum Mishmatch"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2011-11-23
I have installed 11.10 with no issues (apart from getting the wireless to work!) but I can not update..! My package manager tells me there are updates but when I try and download I get the dreaded HASH SUM MISMATCH error message.

Here is the error output - 

[Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/main/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb](http://ubuntu.virginmedia.com/archive/pool/main/l/linux/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb) Hash Sum mismatch
Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/main/g/ghostscript/libgs9-common_9.04~dfsg-0ubuntu11.1_all.deb](http://ubuntu.virginmedia.com/archive/pool/main/g/ghostscript/libgs9-common_9.04~dfsg-0ubuntu11.1_all.deb) Hash Sum mismatch
Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/main/f/firefox/firefox_8.0+build1-0ubuntu0.11.10.3_i386.deb](http://ubuntu.virginmedia.com/archive/pool/main/f/firefox/firefox_8.0+build1-0ubuntu0.11.10.3_i386.deb) Hash Sum mismatch
Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/main/libr/libreoffice/libreoffice-common_3.4.4-0ubuntu1_all.deb](http://ubuntu.virginmedia.com/archive/pool/main/libr/libreoffice/libreoffice-common_3.4.4-0ubuntu1_all.deb) Hash Sum mismatch
Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/main/libr/libreoffice/libreoffice-writer_3.4.4-0ubuntu1_i386.deb](http://ubuntu.virginmedia.com/archive/pool/main/libr/libreoffice/libreoffice-writer_3.4.4-0ubuntu1_i386.deb) Hash Sum mismatch
Failed to fetch [http://ubuntu.virginmedia.com/archive/pool/main/libr/libreoffice/libreoffice-core_3.4.4-0ubuntu1_i386.deb](http://ubuntu.virginmedia.com/archive/pool/main/libr/libreoffice/libreoffice-core_3.4.4-0ubuntu1_i386.deb) Hash Sum mismatch]

I have tried changing download server - to no avail.

Any ideas why this is happening?

---

### Post by bluexrider on 2011-11-23
This happens due to a repository flush. This also usually means there  are going to be updates or new tools very soon in the repo. Flushes do  not take more than 10 minutes, so if you get this error, wait a bit, and  try again.

---

### Post by bigtel on 2011-11-23
I have tried over the past few days, but still get the same message.

The other thing is when I try and install anything through the Ubuntu Software Center I get the message 

**"Package Operation Failed - The installation or removal of a software package failed."**

I have tried installing a few different programs and get the same message. Does this point to a fundamental flaw somewhere with my system?

---

Update

I have now tried deselecting all updates and downloading and installing them one by one - this seems to work apart for the larger files. I.e. Firefox upgrade and main linux image update.

[IMG]http://i41.tinypic.com/2116r0o.png[/IMG]

---

### Post by bluexrider on 2011-11-26
This also may be a slow Internet connection, your modem may be dropping packets, a number of things. 

If you are able to retrieve packages individually it says to me its a connection issue.

---

