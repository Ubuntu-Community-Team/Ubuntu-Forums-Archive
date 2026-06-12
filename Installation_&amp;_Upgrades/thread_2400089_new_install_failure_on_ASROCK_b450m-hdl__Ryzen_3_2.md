---
title: "new install failure on ASROCK b450m-hdl / Ryzen 3 2200g"
date: 2018-09-02
forum: Installation &amp; Upgrades
---

### Post by gmussman on 2018-09-02
Hello,
So, I have no experience in Linux, and this is a first-time computer build for me, using the main board and chip in the title and an SSD hard drive that is also new.  I was going to run Ubuntu (its free, and I'm kind of curious about it).  I made a bootable USB using a mac (formatted USB to FAT, using Etch to create the USB, image is ubuntu-18.04.1-desktop-amd64.iso .   When I power on, I can get to the BIOS, but when I boot from the USB I get the following screens and errors (sorry for rotation on first).  Any idea what's happening here and how to fix it?


[ATTACH=CONFIG]280946[/ATTACH][ATTACH=CONFIG]280947[/ATTACH]

---

### Post by TheFu on 2018-09-02
I'd try setting the BIOS to "safe" values.  If that doesn't work, then I'd start looking through the BIOS settings, reading up on what every one of them means.

And I'd google for the board + ubuntu + install to see if anyone else has reported issues.
While doing that, run through a memtest for 12+ hrs to see if memory issues are any concern.

---

### Post by gmussman on 2018-09-03
Thanks for the reply.  

I've been looking through the manual and I can change ACPI settings, so I'll give that a go.

The BIOS is not picking up the RAM correctly -- it has the frequency wrong, so I'll try the memtest too.

---

### Post by gmussman on 2018-09-03
Well I can't run memtest because I don't have another working 64-bit computer to extract the EXE on.  I'll see if I can find a workaround.

---

### Post by TheFu on 2018-09-03
ryzen is known for being VERY picky about RAM. Is the RAM you have on the approved RAM for the motherboard?   If not, I would try slowing it down first, but expect to return it and buy RAM that is specifically listed on the compatible RAM list from the motherboard vendor.

---

### Post by oldfred on 2018-09-03
The issue may not be ACPI errors, I have Intel and get a couple of those on every boot. But system works ok.

Older Asrock had Asmedia ports. Not sure if just Intel or also AMD. But those ports did not work and even having a DVD drive in Asmedia port prevented boot.

Best to start with UEFI Secure Boot off. May be called "Windows" or "other" where fine print says if using Windows 7 use Other setting. Windows 7 does not support UEFI secure boot.

Also turn off fast boot in UEFI. While reconfiguring system, you want to be able to get into UEFI and one time UEFI boot menu. But fast boot assumes no change, so UEFI does no hardware configuration checks and immediately turns boot to system. And system is reading previous configuration data on drive which then may or may not be correct. And with fast boot, it is so quick you have no or almost no time to press key to get into UEFI to change settings or UEFI boot menu.

---

### Post by gmussman on 2018-09-03
I was worried about the ram -- the MFR part # for my ram was slightly different from the QVL list and I didn't notice it.  UEFI recognizes it, it just runs slow ... I'll probably replace it.

I tried turning off fast boot and secure boot off.  Still crashed with install.  

Just to check, I tried installing windows 10 from another license and it went on fine, no hiccups at all.

---

### Post by wesnewell on 2018-10-06
I've got an Asrock AB350 Pro4 and ryzen 2200g and had a lot of trouble with it. With my pcie tuner cards installed it wouldn't even boot to bios. Bios P5.00 fixed that problem, but trying to install xubuntu 18.04.1 had a double screen, and the system would still hang on boot or screen would be screwed up. IIRC I put the system back on my old Phenon system, installed ukuu and then installed the 4.17.x kernel upgrade, then moved dirves, tuners, etc. back to the asrock system. Still had problems with boot hanging sometimes but resets would finally get a boot and everything after that worked fine. I kept installing the latest kernel and am now running 4.18.12. First, try upgrading the bios. If you can't get 18.04 to install, go back to 16.04 and install it, then use ukuu to install the latest kernel and then do an upgrade to 18.04.1. I also trird a couple of other distros and at least one of them would work ok, but I didn't want to reconfigure my whole server so persisted to get what I wanted. Still hangs on boot sometime, but this is a 24/7 system, so isn't shutdown or rebooted often, so isn't a big deal for me. If I had it to do all over again, I would have just waited for better support of raven ridge cpu/apu's.

---

