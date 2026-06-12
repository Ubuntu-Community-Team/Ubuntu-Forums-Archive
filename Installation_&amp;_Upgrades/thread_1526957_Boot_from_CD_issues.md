---
title: "Boot from CD issues"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by sarmedic603 on 2010-07-08
Hey all, 
I'm trying to install Ubuntu 10.04 on my mom's computer.
She has an e-machines desktop, which was previously running Windows XP. Long story short, it got "some virus", she's re-installed windows a few times, and the virus is still present it seems.
 
I figured I'd install Ubuntu so she has access to email and word processor while I 'purchase' another copy of Windows (read: have time to do the job right).
 
It appears to be a 64-bit machine, to my surprize. I've attempted the following, each resulting in the following error (after BIOS... this appears to be the Bootloader on her machine)
 
```
 
Boot from CD:
 
Intel UNDI, PXE-2.0 (build 082)
Copyright....
 
For Realtek RTL8139(X)/8138/810K PCS Fast Ethernet Controller v2.13 (020326
 
CLIENT MAC ADDR: 00 13 ?? ?? ?? ?? GUID: FFFFFFFFFF-FFFF-FFFF-FFFFFF (not exact - but all "f"'s
DHCP...\|/\|/\| etc... once this times out, the following appears:
 
PXE-E53: No boot filename received
 
PXE-MOF: Exiting PXE ROM.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

```
 
I've tried:
10.04 - 32 bit ( DVD, USB), using Infra Recorder and the Universal USB Installer
 
10.04 - 64 bit (DVD, USB), same as above. (Once I realized it was actually a 64 bit machine)
 
For some reason, Infra Recorder keeps giving errors (on my laptop) when I try to burn a CD... so I'm stuck with DVD/USB for now..
 
 
Any thoughts?
 
I've messed around with BIOS boot orders ad nauseum, burned multiple copies of disks, etc. Nothing seems to be working.

---

### Post by sarmedic603 on 2010-07-08
Does it have something to do with Wubi? Can I remove this?

---

### Post by sarmedic603 on 2010-07-08
I've also disabled PXE, which results in "Boot from CD :", and a blinking _ 
 
The CD drive is whirling and the light is flashing, but that's about it...

---

