---
title: "Can't load from USB on dual boot set up."
date: 2021-08-19
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2021-08-19
Have a new Dell laptop; set up for dual boot between Win10 and 20.04.

I've used 'Start Up Disk' and have U21 ISO on the usb, but cannot get it to auto load after restarting.

I've done the F12 tap, tap, and done what I thought was make USB default, but it still doesn't.

Any help would be appreciated.

---

### Post by oldfred on 2021-08-19
If very new Dell, we have seen 20.04 not work, but 21.04 work.
There will be a newer 20.04, 20.04.3 out soon which also may have improvements.

What model Dell? What video card/chip?
See tea for one's post:
[https://ubuntuforums.org/showthread.php?t=2461231](https://ubuntuforums.org/showthread.php?t=2461231)

And see link below in my signature.

Have you updated UEFI and SSD firmware?
Dell typically needs Intel RST changed to AHCI, but you need Windows  AHCI driver's first.
Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) 
But if you do a safe boot first, then boot to UEFI/BIOS and change to AHCI and finally boot normally, it works
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347) & 
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)

---

### Post by mawil10132 on 2021-08-19
20.04 has been on it for 6 months, works fine. It dual OS, and all I want to do is put 21 on instead of 20.04.  Without losing the Win10.

---

### Post by oldfred on 2021-08-19
How did you make USB live installer.
Some tools make UEFI only or BIOS/CSM/Legacy only installers.
Then you have to boot in correct mode.
But f12 should show you boot options, if in UEFI you have full USB support or allow USB boot setting.

If f12 key not working is f2 also not working to get into UEFI settings?
You then may need full cold boot as you probably have UEFI fast start up on.

---

### Post by tea for one on 2021-08-20
Also, you have backed up all your personal data (from both Windows 10 and Ubuntu)?

---

