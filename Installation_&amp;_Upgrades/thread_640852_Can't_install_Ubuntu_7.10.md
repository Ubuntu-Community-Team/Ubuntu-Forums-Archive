---
title: "Can't install Ubuntu 7.10"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by ingoldsby on 2007-12-14
Hello,

This is my first attempt at installing linux in many many years, and I decided to go with Ubuntu. I downloaded and burned the i386 install disc (at 4x speed) and when I boot up using the disc it starts out just fine.

However when I choose to install ubuntu I get the loading screen and then it drops down to a command line prompt: 
Busybox v1.13 ... 
(Initramfs)

I've tried the i386 install and the amd64 install and I get the same results every time.

I'm running an Athlon 64 3200+, 2gb ram, Nvidia 7800 GS... pretty standard hardware really.

I have 2 SATA raptor drives, my "C" drive (which has xp installed on it) has a 7gb partition set aside as fat32 for ubuntu.

I hope this makes sense, I'm a bit of a linux newbie. Let me know if you need any other information from me.

Thanks in advance!!

Brian

---

### Post by Pumalite on 2007-12-14
Post your specs. You might need the Alternate CD.

---

### Post by ingoldsby on 2007-12-14
> **Pumalite said:**
> Post your specs. You might need the Alternate CD.

Memory (RAM) 		2048 MB
CPU 		AMD Athlon(tm) 64 Processor 3200+
CPU Speed 		2149.2 MHz
Sound card 		SB Audigy Audio [9C00]
Display Adapters 		NVIDIA GeForce 7800 GS 
Screen Resolution 		1680 X 1050 - 32 bit
Network Adapters 		NVIDIA nForce Networking Controller - Packet Scheduler Miniport
CD / DVD Drives 		G: SONY DVD RW DRU-810A
COM Ports 		COM1 | COM2
LPT Ports 		LPT1
Mouse 		16 Button Wheel Mouse Present
Hard Disks 		C: 62.4GB | D: 69.2GB | I: 6.8GB
Hard Disks - Free 		C: 13.5GB | D: 13.5GB | I: 6.8GB
BIOS Info 		ATAT COMPATIBLE 111005 Nvidia 42302e31
Motherboard 		MS-7030

That help?

---

### Post by Pumalite on 2007-12-14
I'd do an md5sum on the iso to be sure, but your hardware looks like it can boot a Live CD. The rule is though, if the Live CD does not work, try the Alternate CD. You could also try some boot parameters first if you are stubborn and patient. Here is a guide and a collection of them. Try them one at the time:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by ingoldsby on 2007-12-14
> **Pumalite said:**
> I'd do an md5sum on the iso to be sure, but your hardware looks like it can boot a Live CD. The rule is though, if the Live CD does not work, try the Alternate CD. You could also try some boot parameters first if you are stubborn and patient. Here is a guide and a collection of them. Try them one at the time:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

Thanks for the help, I will try :)

---

### Post by Pumalite on 2007-12-14
You are welcome. Let me know how it goes.

---

### Post by ingoldsby on 2007-12-14
Grabbed the alternate install, and with the text install I get a little further. However once it needs to access the install disc I get a can not mount install cd error. The disc is there, it got me this far, however it wont work from there on out. I get the same error when I try to verify the disc.

I'm wondering if this is the same issue, just displaying differently because it's the alternate install.

I'm still futzing with boot parameters but not having much luck yet.

---

### Post by RogerMurdock on 2007-12-14
I had a similar problem on an Athlon 64 3000+ system, the exact same error message.  Sadly I did not find a solution to the problem, I ended up finding a different distribution of linux that did boot the live cd, but it still wouldn't install.

This may help though:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084")

---

### Post by WEPrechaun on 2008-07-21
Since we have the same motherboard & difficulty, then I thought that I'd mention that my live cd installation worked fine after I disabled ACPI in the CMOS. After ACPI was disabled, I was able to successfully install Feisty, Gutsy, & Hardy. I hope this helps.

---

