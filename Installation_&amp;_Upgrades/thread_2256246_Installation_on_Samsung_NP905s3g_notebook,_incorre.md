---
title: "Installation on Samsung NP905s3g notebook, incorrect boot manager?"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by siddy123 on 2014-12-10
Hi, Tried to clean install 14.04 onto a Samsung NP905s3g notebook. I can install it but once I reboot or take out the live usb. It loads up
[INDENT]All boot options are tried.
Press <F4> key to recover with factory image using recovery
or any other keys for next boot loop iteration.
[/INDENT]

When going into the Aptio config BIOS boot settings (Samsung BIOS configuration), the windows boot manager is now obviously gone with the windows partition being wiped. there are two other boot options 
[INDENT](IP4 IP4 Realtek PCIe GBE Family)
(IP6 IP6 Realtek PCIe GBE Family Controller)[/INDENT]
But i don't think they would do anything. Booting back into the live USB i can see ubuntu there on the disk.

So my understanding is that Ubuntu itself did install but as of now I don't have anyway to boot into it. (thinking of it as there is no bridge between the BIOS and the OS).

Is there anyway to fix this or am I trapped to reverting back to windows?

Any help appreciated thanks.


Samsung NP905s3g

CPU: nameless Quad-core CPU (up to 1.4GHz)
Graphic: AMD Radeon HD 8250 graphics
Memory: 4GB DDR3L system memory at 1066MHz (on BD 4GB)
Storage: 128GB SSD
Previous operating system(s): Windows 8 -> Windows 8.1 -> Windows 10 preview

---

### Post by siddy123 on 2014-12-11
Bumping. Further information tells me that my bios is a UEFI bios which from some reading may complicate things...

Can somebody direct me or tell how to correctly boot up into Ubuntu. Is there a way to do it whilst in the live demo. I have no Windows OS and don't want to be dual booting. The only way I can access an OS is through the live CD or if installed until I turn the machine off.


here is a link to the boot-repair... [http://paste.ubuntu.com/9481516/](http://paste.ubuntu.com/9481516/)

---

