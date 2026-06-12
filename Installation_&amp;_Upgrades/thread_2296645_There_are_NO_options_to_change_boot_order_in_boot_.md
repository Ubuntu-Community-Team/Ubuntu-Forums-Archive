---
title: "There are NO options to change boot order in boot menu"
date: 2015-09-27
forum: Installation &amp; Upgrades
---

### Post by Rob_R on 2015-09-27
I can't get off the ground to boot from a CD or flash drive.  In my BIOS, there are literally, literally no options to change the boot order.  It only allows me to select "Windows Boot manager."  I can only disable it, I cannot change the boot order.

I started with Windows 8.1 and went to Windows 10.  I'm also working from a little known American made laptop brand Lotus on a Solstice PC [http://www.lotuscomputerusa.com/lotus-laptop-computers-built-in-america/lotus-solstice-550-premium-notebook/solstice-550-s55a01](http://www.lotuscomputerusa.com/lotus-laptop-computers-built-in-america/lotus-solstice-550-premium-notebook/solstice-550-s55a01) . 

I've emailed the manufacturer and he suggested it might be secure boot.  I have since determined that secure boot is not enabled.

---

### Post by grahammechanical on 2015-09-27
I think that you have a UEFI boot system and not a BIOS boot system. There are important differences. Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You will need to follow those guide lines. But it is my guess that you are only seeing an option to load a Windows Boot Manager because Windows is the only OS installed. I think that you need to look for a way to direct the motherboard to load an OS from the optical drive or a USB port. That wiki page speaks of "boot order" tab.

Regards.

---

### Post by oldfred on 2015-09-28
There actually are only several vendors of UEFI/CSM software. What vendor is that?
But I have not kept track of which vendors use which UEFI vendor.

One vendor:
 Technical info on Legacy BIOS and UEFI AMI AptioMar 2012 - 20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

 Acer Windows 8 Video on getting into UEFI
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

Many UEFI in addition to secure boot have settings to enable, or allow USB ports or booting from USB ports. One mfg Acer requires the user to set a supervisory password and then they can change more settings which are required for dual boot.

So review UEFI settings, and sometimes a setting that does not seem related may be.

---

### Post by ubfan1 on 2015-09-28
Is the USB present when you are trying to put it first in the boot order?  An Asus netbook only lists the current possibilities, and if you ever boot without the USB after setting it, it will disappear from the boot order.

---

