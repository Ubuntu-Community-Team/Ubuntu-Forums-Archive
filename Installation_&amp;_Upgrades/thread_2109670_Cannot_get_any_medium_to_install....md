---
title: "Cannot get any medium to install..."
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by bradlees on 2013-01-28
I have tried live cd's and usbs to no avail, in the 32 bit and 64 bit variants. I have plenty of space on the hdd, an amd a4 with plenty of ram, current os in Windows 8. 
 
I cannot get the live cd to run. I am brought to the grub screen and if I select install I get nowhere, just the word ubuntu with the dots below it which eventually freezes. I try to run in failsafe or just run without installing and the same thing happens.
 
I also tried to install on a separate partition that I created using the wubi. It begins installing and then it gets to the point where it says to reboot. I reboot and then nothing. I have tried linux mint to just to see if this worked and I got the same results. 
 
Any ideas? A couple of times I got a message about the hard drive hibernating and to run chkdsk. I did this and still nothing.
 
Any ideas?

---

### Post by dino99 on 2013-01-28
some things to check:

- burning : always burn at the lowest speed (better app used : k3b)
- cd hardware quality (checksum)
- look for possible boot option: google around "ubuntu boot option"

note: if you can use an usb stick its better (burning is quite obsolete nowadays)

---

### Post by offgridguy on 2013-01-28
Not sure what you are using,but it is possible it may be incompatible with linux.
You can check here, if you have a laptop.

[http://ubuntuforums.org/showthread.php?t=1543009&highlight=incompatability+list](http://ubuntuforums.org/showthread.php?t=1543009&highlight=incompatability+list)

---

### Post by Mark Phelps on 2013-01-28
> **bradlees said:**
> ... I also tried to install on a separate partition that I created using the wubi. ..
 
Any ideas?
Wubi does NOT use a separate partition; instead, it installs inside as virtual file inside a Windows partition.

Also, if you DO get the installer to run, do NOT, repeat NOT, use the installer to shrink down the Win8 OS partition to make room for Ubuntu.  Doing that risks corrupting the Win8 filesystem and rendering it unbootable.

Pre-installed Win8 boxes nearly all use UEFI -- whole new BIOS setup.

Suggest you search on this and read through the details before you attempt to force an Ubuntu install.

---

