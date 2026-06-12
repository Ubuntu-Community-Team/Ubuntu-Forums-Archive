---
title: "Windows 8 will not boot after installing Ubuntu"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by mchan985 on 2014-05-13
Hi guys so I had Windows 8 preinstalled on my Lenovo Ideapad p500. So I installed Ubuntu using Yumi and loading off of USB. I made sure to turn off secure boot, fast startup. I even had to turn of UEFI boot so that I could find my Ubuntu install on my USB. So after installing USB Ubuntu works fine no problems. When I go to select the Windows loader option from the grub menu I get the error message saying:

Windows Boot Manager load failed.

Windows Boot configuration file is missing or contains errors. 

From this screen I cannot do anything. I have run Boot Repair on Recommended Repair mode and it has not fixed the issue. The other quirky think is I am able to access the Windows_OS partition from Ubuntu I even copied and pasted some files over to Ubuntu just in case I messed up anything further. I am wondering what my next course of action should be? Any help would be appreciated.

---

### Post by oldfred on 2014-05-13
If you turned off UEFI then you installed Ubuntu in BIOS boot mode. And UEFI and BIOS are not really compatible. Once you start to boot in one mode you cannot switch to the other mode. Or from grub menu booted in BIOS you cannot boot Windows in UEFI. 
You should be able to go into UEFI/BIOS turn on UEFI and boot Windows directly.

Post link to BootInfo report.

Do not reinstall Ubuntu without reading caution in link in my signature. Boot-Repair can convert a BIOS install to UEFI just by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI). If you can boot into Ubuntu you can just do that from inside your install also.

---

