---
title: "How to install Ubuntu on UEFI (Toshiba)?"
date: 2013-08-18
forum: Installation &amp; Upgrades
---

### Post by OlavRB on 2013-08-18
Hi guys!

I need some serious help. I'm rying to install Ubuntu alongside with my W8 on my new computer.
Model is Toshiba satellite p50-a-11j (PSPMGE)

What i've managed is getting to grub menu, where it says "try ubuntu", "install ubuntu" etc. When choosing whichever of these options, the screen gets black and nothing happens.

I am using UEFI boot. I've disabled fast boot, secure boot. I've tried enabling/disabling usb legacy mode. I've disabled/enabled Intel Turbo Technology. NO luck yet..
The memory stick is formatted as a GPT device for UEFI boot by the latest RUFUS (v1.3.4) [http://rufus.akeo.ie/](http://rufus.akeo.ie/). Also tried manually formatting it through cmd.
Same procedure with RUFUS was done when installing clean W8, so.. It should work.

There is no BIOS updates for the computer. I've also tried other linux distros, such as Fedora, Elementary. Same result.


Any suggestions guys? :)


Cheers, Olav

---

### Post by oldfred on 2013-08-18
Some others with similar systems.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Ubuntu on Laptop Toshiba Satellite P75 - Haswell
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by OlavRB on 2013-08-21
> **oldfred said:**
> Some others with similar systems.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Ubuntu on Laptop Toshiba Satellite P75 - Haswell
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

Thanks! Disabling built in LAN was the solution :)

---

### Post by Darknote on 2013-11-23
> **OlavRB said:**
> Thanks! Disabling built in LAN was the solution :)
How did you disable the LAN?

I'm facing the same problem and have the same model. 

Many thanks!

---

### Post by oldfred on 2013-11-23
I am not sure what the NIC - network interface controller is or does in UEFI/BIOS. But that seems to be an issue. 
What is the NIC and is it then not required as it seems to work better off?

---

