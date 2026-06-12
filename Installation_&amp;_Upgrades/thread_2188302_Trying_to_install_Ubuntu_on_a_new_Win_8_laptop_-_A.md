---
title: "Trying to install Ubuntu on a new Win 8 laptop - Acer Aspire V3-772G-982"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by Octoxan on 2013-11-16
So I have the latest version of ubuntu 64 bit on dvd and I'm trying to install it on an Acer Aspire V3-772G-982, but with UEFI and secure boot both ON, I get to the screen that says try or install ubuntu, both lead to an all black screen for forever. Same thing with secure boot off and UEFI off. With UEFI off I can't get into Windows 8, correct? And that's a no go. 

Could someone pretty please help me install this? It's driving me mad.

---

### Post by Octoxan on 2013-11-16
Actually just noticed it said something like "error root not set" or something right before it goes to the try/install/OEM install/check defects screen. Errr...

---

### Post by Octoxan on 2013-11-16
Ha. Apparently it was just that the screen brightness needed turned on. But now it's freezing at 
[    87.615763] RIP nve4_graph_init...
[    87.615764] RSP <ffff88014fe81c10>

---

### Post by oldfred on 2013-11-16
What video do you have, Intel, nVidia or both? If both which is it booting with?

Other Aspire, may have suggestions as vendors often are the same or simlar for similar systems.
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

How you boot installer is how it installs. You will want to boot in UEFI mode if you can at all. A few systems only will let you boot in BIOS/CSM mode and then you can use Boot-Repair to convert to UEFI. But often more settings in UEFI that may be interfering with UEFI boot.

More info in link in my signature.

---

### Post by Octoxan on 2013-11-16
It has both intel and nvidia. No idea which one it's booting with. =/ How do I tell?

It starts to boot into UEFI mode and then it says something about RIP nuvuea or something. 

What do I type in the command prompt exactly to do NOMODESET? Mine goes into the black Try/Install screen, not the one where I can just select nomodeset in the corner.

---

### Post by oldfred on 2013-11-16
If booting with nVidia then nomodeset.

If booting in UEFI mode you get the standard grub menu and black screen. The use e for edit, scroll down to linux line, and replace quiet splash with nomodeset.
Shows both BIOS purple screen and grub menu UEFI boot screen, so you know for sure which way you have booted.
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If Intel you may need one of these settings. And it seems to depend on vendor and model of Intel chip.
      
 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

---

### Post by slinkeey on 2014-03-26
> **Octoxan said:**
> Ha. Apparently it was just that the screen brightness needed turned on.

Thanks for that tip.. That was odd..

My Acer V5-473P-6890 had this problem when trying to boot.

---

