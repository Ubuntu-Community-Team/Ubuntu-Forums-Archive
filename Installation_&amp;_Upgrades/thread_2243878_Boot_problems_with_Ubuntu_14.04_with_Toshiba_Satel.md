---
title: "Boot problems with Ubuntu 14.04 with Toshiba Satellite C55"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by alive2 on 2014-09-11
I installed Ubuntu 14.04 on a Toshiba Satellite C55.  I overwrote Windows 8.1 in so doing b/c it was glitchy and freezing a lot on this pretty new computer with little usage and no downloads.    Now, I cannot boot into Ubuntu.   it reads Start PxE over IPv4.    I tried a lot of sites today.   Did a lot.   Some of the changes worked and the partition looks different, but still not bootable.  Sometimes, repeatedly hitting escape takes me to grub, but grub won't do anything.    Sometimes it won't take me to grub...usually, in fact. 

I know this is not how to present questions in the Ubuntu Forum, but I'm pretty much a noobie.  I'd be okay with just working off the Live disc, but it won't let me use WIFI, and I tried the fixes for that and any that are quick enough to do every Live disc sign-in don't work.    Maybe you'll help me.   Ask me what you need to know and how to get the info and I'll be there.  Thanks,  Alive!

---

### Post by oldfred on 2014-09-11
Is this using internal Intel video or does it have dual video?

Some other similar Toshiba
 TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

