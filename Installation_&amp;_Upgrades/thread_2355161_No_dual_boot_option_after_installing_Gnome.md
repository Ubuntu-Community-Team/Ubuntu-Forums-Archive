---
title: "No dual boot option after installing Gnome"
date: 2017-03-09
forum: Installation &amp; Upgrades
---

### Post by anbu-s on 2017-03-09
On my new Dell E7440 laptop, after installing Win7, I wanted to do the dual boot option with ubuntu. So i've installed 16.04LTS in the same drive with a separate partition

Disk1 size 128gb
Win7 - Disk1, 70GB paritition
Ubuntu - Disk1, 48GB partition

It seemed to have installed fine - but now it boots straight to windows. When i press F12 to the boot menu, i do see ubuntu and windows as options, But even when i press ubuntu, it boots in windows

When i try with live ubuntu USB, it detects and says 16.04LTS is installed do you want to erase and install again.

[http://technozed.com/install-ubuntu-linux-alongside-windows-10/](http://technozed.com/install-ubuntu-linux-alongside-windows-10/)

I tried boot-repair in this page - but since i booted it via live USB, it says its in legacy mode and i cannot repair boot in this mode. How do i fix this?

---

### Post by oldfred on 2017-03-10
You can still run Summary Report.
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

But since new UEFI system, did you install Windows 7 in BIOS or UEFI boot mode?
Default Windows 7 from DVD is BIOS only, you have to copy to flash drive & move a couple of files around to make it UEFI bootable.
And a Windows BIOS install converts a new gpt partitioned drive to MBR(msdos), but does it incorrectly. It leaves the backup gpt partition table. MBR has no backup.

---

