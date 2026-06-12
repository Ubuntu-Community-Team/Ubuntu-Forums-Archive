---
title: "Moving my hard disk to a new desktop."
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by Patrick_Van_Esch on 2014-08-08
Hello,

My old desktop with a 12.04 LTS Ubuntu system on, died.  It is not the hard disk that died, it is the motherboard or the processor.
I bought a new cheap desktop with windows 8 on its hard disk.  Unfortunately, in that new desktop there is only (power) room for one hard disk.
My aim is to take out the windows disk, and put in the old Ubuntu disk.
I'm going to do that this evening.  

But I expect serious difficulties with UEFI.  As I cannot boot with windows (the disk will physically be removed) I don't know how to get access
to the UEFI parameters.  I expect my old ubuntu system not to boot under UEFI.  If it were a bios, I wouldn't be expecting any difficulty, but I expect
nothing to happen with my Ubuntu disk in that machine.

Is there some documentation, are there hints, are there things NOT to do ?
Should I first boot with my windows disk, or not ?

How should I proceed ?

Thank you !

---

### Post by oldfred on 2014-08-08
Currently most UEFI systems have CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
A few tablet devices are locked just like an iPad is and a few new 64 bit systems have a 32 bit UEFI which is not yet available with Linux without lots of effort. Some vendors will cripple a system with a 32 bit boot loader just to lock system.

You also should be able to get into UEFI/BIOS settings, but some systems with a fast boot on in UEFI can only get to UEFI/BIOS settings from Windows. There is fast boot in Windows that should be off.

I have seen users say they just remove a Windows drive and install a new SSD to make a laptop fast. Then restore unused Windows hard drive to sell system.

You may have other settings for video or other boot parameters as now it is new hardware. Unless still nVidia for example it may not boot. And if you had nVidia and new system is AMD it may be a bigger issue. Usually you want to uninstall any proprietary video or other drivers first.
But I moved entire system to a new motherboard and upgraded to a newer nVidia card and it just booted without issue.

---

### Post by ibjsb4 on 2014-08-08
Oldfred is the resident guru on uefi, have a look at his post.

[URL="http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi+oldfred&sa=Search&cof=FORID:9"]http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi+oldfred&sa=Search&cof=FORID:9

EDIT .. I should of reloaded this page before I replied ):P
[/URL]

---

### Post by Jonathan Precise on 2014-08-08
Method 1: Olfred's method:

First, using your windows drive, go to the shutdown options, and while holding the SHIFT key, press restart. This is a trick which gives you a menu with some options. Choose something like "UEFI/BIOS Settings". (Sorry. I don't know the exact name, as I do not use Windows anymore.) Like olfred says, there should be an option to change from UEFI to CSM or Legacy boot. It all depends on how the UEFI stuff is structured. Save changes. Then it should reboot. You can now shut down your system normally.
Insert the ubuntu HDD/SSD. It *should* work, unless the graphics card is different (probably it is), so follow oldfred's advice in that case.

[HR][/HR]

Method 2: Converting ubuntu to UEFI:

Disable secureboot. Then get a boot repair CD. Use boot repair to convert ubuntu install to UEFI: [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode]("https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode")

---

### Post by grahammechanical on 2014-08-08
Turning secure boot off is a good idea as the signed kernel was not needed on your old machine. So, it was not installed. Besides it was not available in 12.04 until 12.4.2 came out.

Regards.

---

