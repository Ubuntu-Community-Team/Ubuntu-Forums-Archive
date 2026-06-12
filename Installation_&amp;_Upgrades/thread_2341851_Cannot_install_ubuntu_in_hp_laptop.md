---
title: "Cannot install ubuntu in hp laptop"
date: 2016-11-01
forum: Installation &amp; Upgrades
---

### Post by hibolonce on 2016-11-01
This is my first time trying to use linux OS, my laptop has installed win10 OS already and I want to try ubuntu alongside it.
My laptop has two disks.The SSD including win10 OS partition(C:\ and an EFI partition([FONT=arial]invisible[/FONT]). HHD including one main partition(D:\ and an OEM partition(E:\,called recoverey).
I have Shrinked 50GB for ubuntu(from D:\,showing "50.00GB unallocated") .
Then I downloaded iso file (16.04-desktop-amd64), checked the MD5SUM and no problem. So I made a USB boot by Universal USB Installer.
Before installation I set boot from USB-HDD,UEFI,secure boot off in BIOS, and get into the first sellection screen, within the options like "try ubuntu without installing","*install ubuntu",.etc
Here is the deadend, no matter which option I chose, it will failed after ubuntu logo disappeared, then display the following information:


(Initramfs) Uanable to find a medium containing a live file system
              [COLOR=#ff0000]scsi 20:0:0:0: rejecting I/O to offline device
              blk_update_request: I/O error dev sdc, sector 0
              buffer I/O error on dev sdc, logical block 0, async page read
[/COLOR]

The red part will repeat every few seconds.
I also tried 16.10,14.04,kubuntu and never made it.
Could anyone help me? Thanks a lot.

---

### Post by ubfan1 on 2016-11-01
Did you try other USB ports on the laptop?  Can you select a "media-check" from the USB choices?  Does the USB work in other machines?  Can you reinstall the ISO onto another USB?  Do you have any USB options in your BIOS/UEFI Settings to alter?

---

### Post by oldfred on 2016-11-01
In addition to ubfan1's questions, what brand/model system? And what video card/chip?

---

### Post by RobGoss on 2016-11-01
Is this a single or dual boot that you're trying to setup?

---

### Post by RobGoss on 2016-11-01
I've read somewhere that it might have something to do with the boot sequence if your current boot sequence is ,USB CD, HD, try changing it to USB, HD, CD and see if that helps

---

### Post by hibolonce on 2016-11-01
Thanks all guys above. Just like [COLOR=#000000]ubfan1 said problem is USB port. 
There are three USB ports on my laptop and two of them are USB 3.0.
I don't know exact reason but my installation always failed on USB 3.0 port.
The only USB 2.0 PORT used by mouse and I ignored it. 
[/COLOR][COLOR=#000000]Now it's done, thanks again.

[/COLOR]

---

