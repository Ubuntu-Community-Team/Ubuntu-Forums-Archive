---
title: "Ubuntu 13.10 fails to boot on Sony VAIO Y with &quot;gave up waiting for root device&quot;"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by piotr6 on 2013-11-08
Hello All!!

I've problem with Ubuntu 13.10 after fresh install. Computer halts during the boot process and i got this:
> (initramfs) gave up waiting for root device. common problems:
- boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait for the right device)
- missing modules  (cat /proc/modules; ls /dev)
alert! /dev/disk/by-uuid/...


Hardware: Sony VAIO VPCYB1S1E with AMD Dual-Core E-350

I've established that:
- there is *no any disk* device in /dev in initramfs - not single disk drive
- LiveCD version from usb stick works fine, disk and all partitions are visible
- windows 7 works as normal
- older versions of Ubuntu (12.10 iirc) and Mint 14 are working fine
- when upgrading from older version, system is broken after dist upgrade
- trying few times with different partitions shemes etc
- 'exit' from initramfs dosn't help
- disk is ok, same problem on fresh and clean ssd drive
- bios reset also dosn't help
- recovery mode from grub also fails
- no new clues from google or this forum

i've been working with linux for many years, but with this i have no more ideas! :(

Thanks,
Peter

---

### Post by heir4c on 2013-11-08
here some old tread with the same message (see second post):
[http://ubuntuforums.org/showthread.php?t=1399810](http://ubuntuforums.org/showthread.php?t=1399810)

---

### Post by piotr6 on 2013-11-09
Hi,

Unfortunately it does not work for me - there is no drive visible for system during boot (/dev/sdXX), so this solution also fails :(

Thanks

---

### Post by heir4c on 2013-11-10
Strange, I have also a E-350 processor and it works fine here.
Maybe you can download the ISO file and make a new install usb. Maybe there are things missing.

---

