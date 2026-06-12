---
title: "Help with dual boot gone SOUR!"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by mancini82 on 2012-11-30
I recently installled ubuntu 12 within hours of receiving my new Windows 8 desktop, with the intention of having a dual boot system..I originally installed Ubuntu from a USB, manually configured the partitions (I believed I resized the Windows partition, and used the space created to make a etc2 file system and a swap partition, then installed ubuntu to the swap partition...

This "worked", insofar that Ubuntu was installed, however there was no boot manager that allowed me to select between the OS's.

If I manually changed the system settings to allow Legacy BIOS, ubuntu was loaded. If I allowed UEFI, windows was automatically loaded...but when I got to the windows8 login screen, the system would hang after I supplied the correct credentials...(I believe I destroyed windows when I resized the partition to make room for linux..)

After that, I panicked and tried to re-install ubuntu from USB using the LVM option, which I believe may have overrode my windows partition!

How can I get my Windows 8 OS back, and have the option to select which OS to boot? I learned the hard way that BIOS is becoming obsolete, and am terribly confused with all  this UEFI talk.

Here is my boot-repair URL: [http://paste.ubuntu.com/1400636/](http://paste.ubuntu.com/1400636/)

Thanks in advance!

---

### Post by darkod on 2012-11-30
1. Stop booting ubuntu from the hdd. The more times you boot it, the less chance to recover the windows partition.

2. Use the ubuntu usb stick in live session (Try Ubuntu), download and run testdisk.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Run the Deeper Search, and look carefully at the discovered partitions. If you don't understand the list, post the screenshot here.

Testdisk can usually recover the partitions.

As for installing UEFI dual boot, you have to boot the usb stick in UEFI mode so that ubuntu installs in uefi mode too. And it has to be 64bit ubuntu, since 32bit doesn't support uefi. Just make sure when booting to select the uefi stick, not the legacy stick.

But that's for later, the first task is to rescue the windows partitions.

And another note. When resizing windows to make unallocated space, use windows Disk Management, not the ubuntu installer. Windows is very sensitive to other programs resizing the system partition. Do the resizing with Disk Management, reboot few times, and then try installing ubuntu.

---

