---
title: "BusyBox Error when installing Intrepid Ibex"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Trekky0623 on 2008-10-30
When I select "Install Ubuntu" from the disk, it hangs after a while (the loading bar freezes and it doesn't do anything).  I tried the "try Ubuntu" option, after a while it went to BusyBox with some timeout errors.  Any suggestions?

---

### Post by ricardisimo on 2008-10-31
Same here:
```
Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)
```
And that's as far as it gets when I choose to try Ibex without installing. I've learned very well not to install until I'm certain my wifi is working. Any suggestions? Thanks.

Here's my lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:08.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:0a.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
```

---

### Post by the_darkside_986 on 2008-10-31
I keep getting BusyBox attempting to boot 8.10 i386 but I'm not sure what the error is. I also tried adding rootdelay=130 option, no difference. It is a SATA drive but I had the same issue with Kubuntu 8.10 RC on an IDE drive.

EDIT: when I boot without quiet and splash the last thing written is something about [sda] Attached SCSI disk and then it goes to busybox. Should I just give up and resize the NTFS partition to take up full disk space? :(

---

### Post by bj0 on 2008-10-31
Did you try adding irqpoll to the end of the kernel arguments?  That's what fixed it for me (sata problem)

---

### Post by the_darkside_986 on 2008-10-31
I tried that but it didn't help. But this problem persisted before and after I installed a SATA instead of classic IDE drive.

---

### Post by fewjr on 2008-11-09
Try pci=nomsi and see if that helps. I had that same issue with Hardy and my sata setup and thats what allowed me to install it. I also set to AHCI in bios. I did not need to do that after 8.04.1-iso was available. Here is the thread:
[http://ubuntuforums.org/showthread.php?t=912681](http://ubuntuforums.org/showthread.php?t=912681)
I know we're talking Ibex but its worth a try.

Good Luck
fewjr

---

