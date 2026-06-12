---
title: "Acer Aspire R3-131T and Ubuntu 15.10 GUI login problem"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by arendvanderkolk on 2015-11-03
Hi,

who can help me with my login problem into the GUI? A still screen, a driver issue?

 I have the correct password since i can login to the CLI via Ctrl - F1

Acer Aspire R3-131T and Ubuntu 15.10
lspci -knn |  grep VGA
driver for VGA compatible controller [0300]: Intel Corporation Device [8086:22b1] (rev 21)
VGA compatible controller: Intel Corporation Device 22b1

Who can help?

---

### Post by oldfred on 2015-11-04
You may need a boot parameter:
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

You add it like you would add nomodeset which is usually for nVidia or AMD.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If only Ubuntu you have to hold shift if booting in BIOS mode, or escape key if booting with UEFI.

---

### Post by arendvanderkolk on 2015-11-04
Hi Odfred,

I have entered all parameters at 'set kernel parameters' when starting up.

Although i see a whole list of OK's now scrolling by, the result is unfortunately the same.

This is what i see: [https://youtu.be/sAf-kyD6_6E](https://youtu.be/sAf-kyD6_6E)

Any thoughts? How can i determine if i need a proprietory driver. How does that work?

cheers,

Arend

---

### Post by oldfred on 2015-11-04
I thought your model only had Intel.
So one of the Intel options should help.

How much RAM?
On lightweight systems, often the lighter weight flavors like Xubuntu or Lubuntu work better.

---

### Post by arendvanderkolk on 2015-11-05
Hi Odfred,

It has 4Gb ram. I already tried other Xubuntu with the same result.

---

### Post by oldfred on 2015-11-05
Most of these Acer threads are on the supervisory password & setting trust, but some also go into more detail. Not sure which ones, now though.

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Acer Aspire E15 will not dual boot
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

---

