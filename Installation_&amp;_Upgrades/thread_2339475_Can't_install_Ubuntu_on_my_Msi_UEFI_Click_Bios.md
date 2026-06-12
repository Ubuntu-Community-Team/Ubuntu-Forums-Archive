---
title: "Can't install Ubuntu on my Msi UEFI Click Bios"
date: 2016-10-09
forum: Installation &amp; Upgrades
---

### Post by marcop2 on 2016-10-09
Hi all.
I'm trying to install Ubuntu x64 on my desktop computer (working with UEFI)

when i've tried launching the os installation (via usb mounted with Rufus) this has no worked.
The error that came out is: 

```
Error: invalid sector side s-1.
alloc magic is broken at 0x80d3bbc0: 80c844c0
Aborted. Press any key to exit.
```, or few times, randomly (seen by me)

as i read i have disable the Secure Boot, and the fast Boot.

Once another error comes out: Uncompression error -- system halted
Going Crazy :confused:

Ty for you help. Just ask for more info or for output code 

P.s. I don't want to do a dual boot, want to install Ubu as main os

---

### Post by oldfred on 2016-10-09
MSI motherboard or system? Details on specs, video & drive.
Make sure you have newest UEFI from vendor.

       [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[URL="http://ubuntuforums.org/showthread.php?t=2303544"]http://ubuntuforums.org/showthread.php?t=2303544
[/URL]
 MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878) 
      
 Disable MSI Z87 fast boot to get it to work
[http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725](http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725) 
    


[URL="http://ubuntuforums.org/showthread.php?t=2303544"]
[/URL]

---

### Post by marcop2 on 2016-10-12
Ty, your guides help me to solve the proble. Done!  :guitar:

---

