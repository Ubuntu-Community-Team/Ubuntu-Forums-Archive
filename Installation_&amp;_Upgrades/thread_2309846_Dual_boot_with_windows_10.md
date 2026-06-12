---
title: "Dual boot with windows 10"
date: 2016-01-13
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2016-01-13
Folks,

I've installed windows 10. I would now like to install the latest ubuntu lts version. My system has 2 disks and my intention is to install ubuntu on the second disk.

Are there any pitfalls in doing this? 

All information you can provide will be gratefully accepted.

Regards,

Bob

---

### Post by Bucky Ball on 2016-01-14
None that I can think of. If you can pull the Windows disk out, install Ubuntu, put the Windows disk in, then run in a terminal in Ubuntu:

```
sudo update-grub
```

Reboot when that is finished and grub should have picked up Win, it should be selectable on the grub list at boot, and all should be good.

To remember: Check what mode Windows is installed in. It is probably UEFI. Whatever Win is installed in, install Ubuntu in the same mode. Good luck.

---

### Post by oldfred on 2016-01-14
Is system UEFI?
And then is Windows installed in UEFI or BIOS? Just be sure to install Ubuntu in same boot mode as Windows.
Whether UEFI or BIOS, you do need to make sure you have fast startup off in Windows.

If you do not want to unplug drive which is safest way, you can use Something Else and be sure to install grub2's boot loader to Ubuntu drive if BIOS. With UEFI it will just install to the ESP - efi system partition on sda.
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
      
 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

With second drive you can ignore all the instructions on changing Windows  size. But everything else applies. Windows 10 should be the same as Windows 8 instructions.

---

### Post by bobmac on 2016-01-15
Folks,

Not being a guru I've no idea what UEFI is or where to find out if windows 10 has been installed in it. Any help gratefully appreciated

Regards,

Bob

---

### Post by oldfred on 2016-01-16
Lots of details and even links to explanations of UEFI terms in link in my signature below.

Post this from Ubuntu live installer's terminal (you can copy from here to terminal):
       sudo parted /dev/sda unit s print

If you have gpt partitioning then it is a newer UEFI system. All systems with Windows 8 or later pre-installed use UEFI.
If you have MBR(msdos) partitioning then you have the 35 year old BIOS/MBR configuration. Most Windows 7 systems were BIOS and upgrades to Windows 10 would still be BIOS/MBR based.

---

