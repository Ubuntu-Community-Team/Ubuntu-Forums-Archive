---
title: "Can't boot 64-bit lubuntu"
date: 2018-11-25
forum: Installation &amp; Upgrades
---

### Post by jimi223 on 2018-11-25
I have a 10-year old Fujitsu Lifebook with a dead hard drive, and have been using a live USB version of Lubuntu to great effect.
However, I'm pretty sure I'm running the 32-bit version, and I have a need to run the 64-bit version (to run Chrome Developer tools).
I downloaded the 18.10 64-bit iso and created a boot USB with Startup Disk Creator, but when I try to boot I get:

Could not get fio for li->DeviceHandle: Unsupported
 Failed to find fs: Unsupported
Failed to load image \EFT\BOOT\grubx64.efi: Unsupported
start_image() returned Unsupported

I tried the 18.04 64-bit iso, and I get the same message but with "Unsupported" replaced by "Unknown parameter".  I also tried making these with Rufus on Windows, got the same thing.  Also tried some dd commands I found, and got the same results.  I did notice with Gparted that it was creating a partition to put the data in, and read somewhere there shouldn't be a partition, but Rufus and Startup Disk Creator were making it that way, so I figured that was correct.

Thanks in advance.

---

### Post by slickymaster on 2018-11-25
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by TheFu on 2018-11-25
Are you certain that machine supports 64-bit OSes?  10 yrs ago may have still been 32-bit for hardened laptops.

---

### Post by jimi223 on 2018-11-26
Good point.  It's a Fujitsu Lifebook T731.  Some googling turned up this, which indicates that it could run 64-bit Windows 7 and 8.
[http://webcache.googleusercontent.com/search?q=cache:a2Ucc4XJJ7MJ:support.fujitsupc.com/CS/Portal/supportsearch.do%3Fsrch%3DDOWNLOADS%26Series%3DT%2520Series%26Model%3DT731%26ProductType%3DNotebook%2520PC+&cd=2&hl=en&ct=clnk&gl=us&client=ubuntu](http://webcache.googleusercontent.com/search?q=cache:a2Ucc4XJJ7MJ:support.fujitsupc.com/CS/Portal/supportsearch.do%3Fsrch%3DDOWNLOADS%26Series%3DT%2520Series%26Model%3DT731%26ProductType%3DNotebook%2520PC+&cd=2&hl=en&ct=clnk&gl=us&client=ubuntu)

---

### Post by oldfred on 2018-11-26
It must be less than 10 years old. It says it has an earlier version i5 CPU. Those normally are UEFI systems.
But you probably also need to update UEFI.

It looks like you are trying to boot in UEFI mode. That probably should work, but you may need CSM mode since older system.
  CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Some older threads, may be similar issues.
      
 Some systems require password to turn off UEFI
Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)
 Fujitsu Lifebook A512 [SOLVED] Dualboot pre-installed win 8.1 and Ubuntu 14.04.1 
[http://ubuntuforums.org/showthread.php?t=2254442](http://ubuntuforums.org/showthread.php?t=2254442)

---

### Post by TheFu on 2018-11-27
I have a Dell laptop with that same i5-2540M CPU.  It most definitely **DOES NOT** have UEFI. Mine is from 2010, before UEFI was mainstream.  It is 64-bit.

Trying to install UEFI on a non-UEFI system won't work. I would try installing without UEFI.

---

### Post by janlegein on 2019-03-18
Jimi, did you get this solved? I get the same boot problem with exactly the same messages during startup.

---

### Post by monsignor on 2019-11-09
There is a bug related to this problem: [https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1810070](https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1810070). 

Please mark it "affects me too" to increase the chance it's getting resolved.

---

