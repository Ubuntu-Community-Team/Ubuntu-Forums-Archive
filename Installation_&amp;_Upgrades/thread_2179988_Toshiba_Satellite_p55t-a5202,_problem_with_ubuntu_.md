---
title: "Toshiba Satellite p55t-a5202, problem with ubuntu live cd"
date: 2013-10-10
forum: Installation &amp; Upgrades
---

### Post by hellonearth7171 on 2013-10-10
when i boot up from the live cd to install ubuntu where its supposed to be purple in the background its just black it says install ubuntu and try ubuntu but when i click one it goes to a black screen for awhile then it restarts my laptop i have a toshiba satellite p55t-a5202 intel core i5 cpu intel hd 4000 graphics and its a touchscreen laptop can anyone tell me what the problem is i know its not the cd because i made a bunch of them with different isos to make sure it wasnt that

---

### Post by oldfred on 2013-10-11
Welcome to the forums.
Purple screen is BIOS boot, Black screen with grub menu is UEFI boot. If Windows is UEFI you do want UEFI boot but may have to manually add nomodeset or other boot parameters to grub linux line.
At grub menu press e for edit, scroll to linux line and replace quiet splash with nomodeset. If only Intel graphics you may need other settings.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 Some other boot options for Intel graphics
acpi_osi=Linux  acpi_backlight=vendor

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

Some with very new systems find the beta 13.10 works better. But it still is beta.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by joel-schopp on 2014-03-27
> **hellonearth7171 said:**
> when i boot up from the live cd to install ubuntu where its supposed to be purple in the background its just black it says install ubuntu and try ubuntu but when i click one it goes to a black screen for awhile then it restarts my laptop i have a toshiba satellite p55t-a5202 intel core i5 cpu intel hd 4000 graphics and its a touchscreen laptop can anyone tell me what the problem is i know its not the cd because i made a bunch of them with different isos to make sure it wasnt that

I experienced the same problem with 13.10, just tried the 14.04 26-Mar-2014 nightly and it works without a hitch.  14.04 should be out in a few days and the nightlies seem very stable at this point.

---

