---
title: "I need help to create a bootable ISO usb for Windows 11PRO"
date: 2023-12-01
forum: Installation &amp; Upgrades
---

### Post by mugwump40 on 2023-12-01
Well, the title says it all.  I have a new "Mini" PC with 500GB SSD and 32GB of ram.  It's running a RYZEN 7 chip. I've tried everything I can to make a bootable ISO for Ubuntu but Windows 11 PRO won't boot from the USB.  I've even tried Rufus, but I have to admit I haven't found out how to get the options set..  ANY help will be appreciated!!!

---

### Post by guiverc on 2023-12-01
You gave no specifics as to what Ubuntu product (Core? Server? Desktop? or *flavor*?) you're trying to write, nor what release.

During the *groovy* cycle (20.10) some changes were made to the ISOs that can cause issues with some writing software (*that doesn't just clone the image to the media, but reformats it*) though using updated software will usually prevent issues such as this, and if you just *clone* ISO to media no problems will occur regardless of release.

Secondly, are you sure you waited long enough. Some machine *firmware* has *bugs* in the code that can cause external media to often take more than 10 minutes to boot, which isn't a problem on a newly purchased machine as the OS is pre-installed, and isn't often noticed until you try and replace that original OS. Sure you can re-format the ISO so it'll boot faster, but that will have consequences that the ISO can't be used on other hardware, and given we don't install an OS often, my preference is to just be patient.

Some links

- [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)
- [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)
- [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

all being QA tested for Ubuntu ISOs written on Ubuntu (or other GNU/Linux), Mac OS, or Windows.

Did you verify the ISO after download?  It's cheap insurance in my view

- [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)

Further did you verify the ISO was written correctly to media?  (*this should generally not be done with the writing software itself, but subsequent to that, and here details do matter as older releases had a different method of checking than newer releases*).

There can also be other issues relating to hardware (*which require specific types of boot*; eg. *did you try safe graphics*), however you gave no product & release details. Further some releases are available with different kernel stacks (*especially useful on old hardware where the oldest kernel stack ISOs will be better, and newer hardware where you want a recent kernel stack ISO*), but again you gave no specifics of product/release or ISO attempted.

Don't forget there are many types of ISO files, Ubuntu ISOs should be written using methods intended for Ubuntu ISOs, just as other ISOs should be written using methods intended for those often different types of ISO files.

---

### Post by mugwump40 on 2023-12-02
I'm trying to load Ubuntu Desktop - Cinnamin.  It has nothing to do with Ubuntu.....Windows won't even look at the USB.  Regardless how I set the BIOS, it ignores trying to boot from the USB and boots completely normal, straight to Windows 11.  The machine boots Windows amazingly fast....less than 10 seconds.  Yes, I have a good ISO.  The problem is 100% Windows.

---

### Post by tea for one on 2023-12-02
> **mugwump40 said:**
> The machine boots Windows amazingly fast....less than 10 seconds.
Windows 11 > Power Options > Disable Fast Startup
Uefi Settings > Disable Fast Boot

When these options are enabled, the PC will boot quickly and it may prevent access to one-time boot menu via dedicated keys.

---

### Post by ubfan1 on 2023-12-02
Yup, probably the faststartup, but to answer the question of how to make a Windows USB on Ubuntu (and even use it on older machines):
[COLOR=#3D3D3D][FONT=&quot]Assuming you can't simply use Microsoft's Media Creation Tool (maybe won't do the ISO you want,...)

Recent experience just after Windows 23h2 ISO was publicly released

Setting up a Windows install USB can be a real pain, since the easy way[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]using Media creation tool didn't pick up the 23h2 ISO I wanted, and of[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]course, it cannot use a local ISO that I'd already downloaded.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]Normally, I'd use dd to just block for block copy the ISO to the USB,[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]but that wont boot (Thanks Microsoft).  You have to make a[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]filesystem on the USB to copy the ISO files -- can't use ntfs, gotta[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]use FAT and woopsie, there's a 5.3GB file in the ISO, which is illegal on FAT.
Use another tool,[/FONT][/COLOR][COLOR=#3D3D3D][FONT=&quot] wimsplit, to split that one up).  So, finally a USB that[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]boots the windows installer I want.[/FONT][/COLOR]

[COLOR=#3D3D3D][FONT=&quot]Of course, it boots on the old machines, but rejects them as[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]unsuitable. Trick is to immediately shift-F10 to pop up a cmd window, regedit a new[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]key, Local_machine/system/Setup/LabConfig and add dword(32) items[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]BypassTPMCheck, BypassRAMCheck, and BypassSecureBootCheck with value=1.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]Then the install went just fine on both old machines.  Happily, their[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]existing activations carried through, even the Win 7 pro I'd used on[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]one of them.  Should be all set for two more years on those laptops.
Additionally, the dual boot Ubuntu setup on each machine was not touched.

[/FONT][/COLOR]

---

### Post by mugwump40 on 2023-12-02
Problem solved!  Just download Etcher from the Ubuntu site and follow the instructions.  Very easy and fast.  Windows 11 is a pain as Microsoft does everything they can to keep you in their OS, including disabling the ability to boot from a normal USB stick.  I'll plug my new PC....Beelink,  AMD RYZEN 7.  I had a  AMD 6 core FX  and this new chip is much FASTER.  I have a 1 Gb internet connection and this thing loaded and set up Ubuntu in less than5 minutes.

---

