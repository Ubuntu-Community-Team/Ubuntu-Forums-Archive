---
title: "Ubuntu 9.10 ntfs_pread failed"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by fuzeman on 2009-12-28
Hi
After installing Ubuntu 9.10 from Wubi i rebooted and pressed down hit enter on Ubuntu. After the Logo Comes up and flashes it brings up these messages:
```

Completing the Ubuntu installation.
For more installation boot options, press 'ESC' now...
0
   [Linux-bzImage, setup=0x3400, size=0x3b26e0]
   [Initrd, addr=0x37a72000, size=0x57d098]
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either incosistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g .
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Cannot mount /dev/sdc1 on /isodevice

(initramfs) 


```

Any way i can fix this? i tried a 'chkdsk /f' in Windows it said it needed to schedule it so i did, rebooted it then did a chkdsk, so i rebooted into windows again, then rebooted into ubuntu and it brings this up. Any Ideas?

Thanks

---

