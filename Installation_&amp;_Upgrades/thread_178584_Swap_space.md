---
title: "Swap space"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by jon_z on 2006-05-17
If i removed a partition on my hard drive and freed up my space, can i delete my swap partition, add the extra space and make a new swap partition and sucessfully work? 

*also*: can i have two installs of linux share the same swap space? both ubuntu.  one kubuntu, one ubuntu?

Another question..  ? Can two linux machines be hooked together VIA USB cable?  I want to have my one computer just a media computer for me and play music through the usb cable, is that feasable?

---

### Post by dickohead on 2006-05-17
You would need to edit /etc/fstab and make sure that the new swap partition was noted. For example: if your current one is /dev/hda2 and you made a new partition, your new swap MAY be /dev/hda4 and you would need to alter that in your fstab file.

As for using one swap partition for multiple versions of linux - GO FOR IT! It works fine on my computer (Breezy, Dapper and SuSE). The swap partition doesn't even need to be on the same hard drive, and it can even use multiple swap partitions.

:)

---

### Post by jon_z on 2006-05-17
That solved the Swap space problem, i have two ubuntu's running off of it.

Next question, is it possible to network via USB? or would buying another NIC be the best bet?

---

