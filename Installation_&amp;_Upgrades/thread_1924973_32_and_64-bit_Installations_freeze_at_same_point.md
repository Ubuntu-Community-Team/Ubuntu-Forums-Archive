---
title: "32 and 64-bit Installations freeze at same point"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by h4pless on 2012-02-13
I have tried both the 32-bit and 64-bit installation CDs for ubuntu 11.10 and both have frozen at:
  [16.234993] usbhid: USB HID Core Driver
I have tried several different disks  with several different ISOs for each version of the OS and always have the same result. Does this mean Ubuntu will not work with my computer or is there a work around for this issue? The system is a brand new MSI GT683DX built by Prostar and has had no issues with windows so far.

---

### Post by xycris on 2012-02-13
hi h4pless,
try doing this: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by h4pless on 2012-02-14
Thanks xycris,

The nomodeset option got me pass the freeze point so I was able to install. Seems like it must have been some issue with the graphics card's compatibility. After the install, I changed the grub file so that nomodeset was default and then installed the correct display drivers from nvidia and now everything seems to be working great.

Thanks again!

---

### Post by xycris on 2012-08-07
i know this is a late response.

no problem. glad to be of help. maybe you have nvidia optimus on your hardware. if you do, you might be interested in the bumblebee project especially if your unit uses a lot of power and heat is an issue.

nvidia optimus is present if you have both nvidia and intel graphics into your hardware. that is what they thought of solving power issue but unfortunately it is not yet readily supported under the linux kernel.

---

