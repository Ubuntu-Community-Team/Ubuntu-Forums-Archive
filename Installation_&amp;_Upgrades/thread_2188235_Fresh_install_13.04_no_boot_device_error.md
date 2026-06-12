---
title: "Fresh install 13.04 no boot device error"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by ptaylor168 on 2013-11-16
Hi all, Im hoping for some newbie support on yet another "no boot device found" error after installation.

I am attempting to install Ubuntu 13.04 as a single OS from the amd64 image. The install completes but on boot i get the above error.

I have booted "live" ubuntu and run boot-repair which had returned the following error log


[http://paste.ubuntu.com/6425511/](http://paste.ubuntu.com/6425511/)

Thanks in advance

---

### Post by mörgæs on 2013-11-16
Hi, welcome to the fora.

Slightly off topic: Why did you install 13.04, which has only a couple of month left of support, and not 13.10?

---

### Post by ptaylor168 on 2013-11-16
I thought I'd read it that 13.10 will be supported for the next 9 months whereas 13.04 was a long term release, maybe I will try 13.10 and report back

---

### Post by fantab on 2013-11-16
> **mörgæs said:**
> Hi, welcome to the fora.

Slightly off topic: Why did you install 13.04, which has only a couple of month left of support, and not 13.10?

Good Question.
If its possible download and install the latest 13.10, 13.04 will end support in January 2014.

> BootOrder:** 0002,0001**
Boot0001* Hard Drive	BIOS(2,0,00)
Boot0002* UEFI: SanDisk	ACPI(a0341d0,0)PCI(13,2)USB(5,0)HD(1,185a30,11c0,71bafca0)

Presently your Sandisk USB device is set as primary boot device, when it should be the Hard Drive.
Go into your BIOS/UEFI and change the boot order to boot Hard Drive [0002] first.

---

### Post by ptaylor168 on 2013-11-16
Yep that was to boot Ubuntu from the USB to run boot repair, tried to boot the machine with the hdd as boot option 1 and get the error as above

---

### Post by ptaylor168 on 2013-11-16
Well that's frustrating, I've spent days digging for answer on this and simply giving up on 13.04 and installing 13.10 worked, thanks for the suggestions guys!

---

