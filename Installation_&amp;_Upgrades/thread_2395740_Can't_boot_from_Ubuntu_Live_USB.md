---
title: "Can't boot from Ubuntu Live USB"
date: 2018-07-06
forum: Installation &amp; Upgrades
---

### Post by osakawilson2 on 2018-07-06
When I set up 18.04 I somehow partitioned the os a small amount of memory and left a huge chunk unused. I want to fix that. 
I used Startup Disk Creator to install Gparted Live to a USB and tried to install that. On boot,  it went straight to Ubuntu on my hard disk. 
I used Startup Disk Creator again to install a Bionic Beaver .iso to a a USB and tried to install that too. It went straight to Ubuntu on my hard disk.

I accessed the BIOS boot switcher and tried each of the possible USBs on the list, but they all went straight to Ubuntu on my hard disk.
I went into the advanced BIOS settings and changed the boot order. It went straight to Ubuntu on my hard disk.
I removed my hard disk from the boot order in the advanced BIOS settings. It went straight to Ubuntu on my hard disk.
I tried changing USB ports and tried a few of the above things. It went straight to Ubuntu on my hard disk.

Any ideas? I've completely cleaned the system of any files, so I would be fine completely reinstalling again, if that is possible. 
I've now installed the same Beaver file to an SD and will try to boot from that.

---

### Post by westie457 on 2018-07-06
Hello
Have you tried mkusb to create the install media? I have found this to be more reliable than 'Start-up Disk Creator'. [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
Another good tool is 'Etcher' available here. [https://etcher.io/](https://etcher.io/)

---

### Post by yancek on 2018-07-06
If you originally had a usb/DVD which you used to install Ubuntu 18.04, you already had GParted on that device.  Your problem is in the BIOS setup settings and boot options and the change you make are either not correct or are not being saved.  Otherwise it would not boot the installed Ubuntu.  Posting the manufacturer name might help as someone here may know which settings need to be changed to access usb.as each manufacturer varies.  Was this a UEFI install of Ubuntu?  Is your computer EFI capable?  Have you tested the usb of GParted/Ubuntu on another computer?  Results?

---

