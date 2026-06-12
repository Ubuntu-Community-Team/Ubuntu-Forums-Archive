---
title: "Can not boot to cd -BIOS"
date: 2016-10-05
forum: Installation &amp; Upgrades
---

### Post by manefan on 2016-10-05
Bought a lenovo G50-80, i7 5500u, win 8.1, upgraded to win 10. I want to Install ubuntu as a dual boot. When I go to BIOS (insydeH20 5.0), after I disabled secure boot,  it still doesn't show me the option to boot from hard disc or cd or hard disc (!) It also doesn't have an option to add boot. The only order that I can change is between the <windows boot manager> and <EFI PXE network>. Here is the boot menu:

Boot mode   [UEFI] 
Fast boot     [Disabled] 
USB Boot.    [Enabled] 
PXE boot to LAN [Enabled] 

EFI
Windows boot manager (wdc wd10...)
EFI PXE network

---

### Post by farrinux on 2016-10-06
I can not comment on your BIOS boot problems as I do not have that hardware to look at.  However I noticed that it does have USB boot enabled.  Why not just make a bootable usb stick and use that to install ubuntu. I have included two links below.

[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu]("https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu")

[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows]("https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")

---

### Post by ubfan1 on 2016-10-06
After you install Ubuntu (in UEFI mode like Windows) you should see it as an EFI choice.  Do you have a bootable CD present when you run the BIOS/UEFI settings?  Maybe it only shows up if present.

---

