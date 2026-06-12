---
title: "is there a way to have an option upon which drive to boot from?"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by Cyberpawz on 2012-06-13
Before I go forward, I am looking at creating a boot option upon start up, either the OS on my laptop, or the installer drive I have on my laptop. 

Basically I want to make it so after a few seconds (5 or so) the laptop will automatically go to the installed OS, otherwise you choose to go to the installing partition. 

I hope this makes sense...

---

### Post by oldfred on 2012-06-13
Is this another hard drive or flash drive?

You can add custom boot entries into 40_custom to chain to another drive, partition, install or even ISO. You can use grub customizer to change boot times easily or manually edit the grub file.

gksudo gedit /etc/default/grub
# after any change run this to update grub.cfg (menu)
sudo update-grub

HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

You can just chainload to another MBR, but boot drive in grub is always hd0, and if a removeable drive number may change. If it does you can manually edit grub as you boot to change.

Add entry below 
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

```
menuentry " Chainboot hd1" {
set root=(hd1)
chainloader +1
}

```

---

