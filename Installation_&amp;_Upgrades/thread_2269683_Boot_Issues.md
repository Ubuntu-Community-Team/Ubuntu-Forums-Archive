---
title: "Boot Issues"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by Lester_Flax on 2015-03-17
[FONT=book antiqua]I have a similar issue. This is an old Motherboard without any reference to UEFI. I tried four hard drives and got the /dev/sda on /Media failed error.
Also Unmount: Can't unmounts media invalid argument
Mounting: /dev /fd0 on / media failed: no such device or address.
I bought a new 1 TB SATA drive and created a 350GB partition on which I installed Windows 10 Preview.  Rebooting and starting the installer, I get to the ENGLISH prompt, then it drops to a black screen with the errors stated above? 
I have downloaded the file three separate times and burned 3 separate copies, all of which return the same error.
Please advise what I might be doing incorrectly. I have done numerous previous Ubuntu installs.

carib909.



[/FONT]

---

### Post by oldfred on 2015-03-17
Please to not hijack another thread. 
Moved to your own thread as the issues are not at all related to that which is UEFI.

What video card/chip do you have? 
Were drives ever part of RAID? gpt partitioned and Windows converted back to MBR?

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you have a mulitple drive system, best to have Windows on one drive and Ubuntu on another. 
Also even if Windows is in BIOS mode you must turn off fast boot.
      
 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

