---
title: "Ubuntu Installation error"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by coolhangingsam on 2011-08-14
Hi,
i m not able to install ubuntu 11.04 inside windows 7 32-bit, the error which i m getting is depicted below.....kindly help me i will be eagerly wait for the solution...
thanks

>>command=C:\Windows\System32\bcdedit.exe /set {ffe37e88-1f94-11df-8c57-ec021f456b2b} device partition=S:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.

>>stdout=

---

### Post by Rubi1200 on 2011-08-15
Hi and welcome to the forums :-)

Check in Windows in the Disk Management utility and see if your disks are labeled as Basic or Dynamic.

If the latter, you will not be able to install Ubuntu, Wubi or normal, because there are potential problems that can seriously damage Windows if you attempt such an install.

If the disks are not labeled Dynamic, then please post the results of the boot info script. There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by coolhangingsam on 2011-08-16
Isn't there any other way apart from changing from dynamic to basic... in my case ubuntu is installed properly when installed in volume C (volume having windows 7) but gives the above error when installed in any other volume...

---

### Post by coolhangingsam on 2011-08-16
And All the volumes(C, S, etc) belong to the same dynamic disk...

---

### Post by bcbc on 2011-08-16
> **coolhangingsam said:**
> Isn't there any other way apart from changing from dynamic to basic... in my case ubuntu is installed properly when installed in volume C (volume having windows 7) but gives the above error when installed in any other volume...

This is dangerous - because windows allows it, and because C: is in the MBR partition table, it seems to work. But Ubuntu won't see the other dynamic drives and there is a potential for loss of data.

(Note it is actually Windows' bcdedit giving you that wubi install error - which is a good thing). If I were you I'd try out Ubuntu in a virtual machine (or install it direct to an external or additional hard drive and don't mount the windows dynamic partitions.)

---

### Post by Rubi1200 on 2011-08-16
I second bcbc's recommendations. Do not try and install with Dynamic disks. An external HD is cheap enough these days that to get one and install and run Ubuntu from there would be the safest option.

Or in a virtual machine as suggested.

---

### Post by coolhangingsam on 2011-08-20
thnx a lot...

---

