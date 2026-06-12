---
title: "Nervous on how to install Ubunto with Win 10 and UEFI"
date: 2017-03-19
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2017-03-19
Hello All,
Apologies if this is basic, but I want to be really sure I get this right, without making my PC unusuable.

It's running Windows 10, WIth ASUS UEFI Bios.
I've found the section on Secure Boot, which points at the Windows Boot Manager (SAMSU
But as there's no alternative under that menu, I'm reuctant to try it in case I make the PC unbootable,

If someone can point me at how to safely install Ubuntu on this computer, without wiping Windows 10, I'd be very grateful.

Thanks,
Nick

---

### Post by kansasnoob on 2017-03-19
Could you please provide more details regarding the computer or motherboard? An actual model # or such would give us something better to work with than just providing generic instructions.

---

### Post by starbase1 on 2017-03-19
> **kansasnoob said:**
> Could you please provide more details regarding the computer or motherboard? An actual model # or such would give us something better to work with than just providing generic instructions.

Not sure if this will help - it's a Chillblast custom build, from here in the UK. Not a standard model.

Latest version of Win10 64 bit installed (ugh)

The bios is the ASUS UEFI BIOS Utility, I'm looking in the advanced mode, boot section.

ASUS Z170-A motherboard
Intel Core i7 Skylake CPU.

Does that cover it?

Thanks,
Nick

---

### Post by starbase1 on 2017-03-19
One other thing, In the boot menu, the only option is:

Windows Boot Manager (SAMSUNG MZVPV256HDGL-00000)

---

### Post by yancek on 2017-03-19
The link below is the Ubuntu documentation on dual booting with windows using UEFI. You might take a look at the ASUS manual if you have it regarding BIOS options for UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ubfan1 on 2017-03-19
Here's another helpful link:
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
The Asus may not keep a bootorder with USB first if the USB is removed or changed.  UEFI install on an older Asus netbook had no particular issues.

---

### Post by starbase1 on 2017-03-19
> **ubfan1 said:**
> Here's another helpful link:
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
The Asus may not keep a bootorder with USB first if the USB is removed or changed.  UEFI install on an older Asus netbook had no particular issues.

Thank you both, I'll take a look and see if I can understand that...

Nick

---

### Post by kansasnoob on 2017-03-19
I found the full .pdf users manual for that motherboard:

[http://dlcdnet.asus.com/pub/ASUS/mb/LGA1151/Z170-A/E10611_Z170-A_UM_V2_WEB.pdf?_ga=1.207135131.984862890.1489163930](http://dlcdnet.asus.com/pub/ASUS/mb/LGA1151/Z170-A/E10611_Z170-A_UM_V2_WEB.pdf?_ga=1.207135131.984862890.1489163930)

It's 130 pages so it takes a bit to open. If you jump to page 103 (section2-51) that's where the various boot options begin. On page 106 (2-54) it shows settings for CSM (which I doubt you'll need - you just have to **be sure that the Ubuntu live USB/DVD boots in UEFI mode**) and Secure Boot. I think what they say there about Secure Boot is pretty much self explanatory. I've not encountered any problems installing Ubuntu 16.04 with Secure Boot still enabled but you should read:

[https://help.ubuntu.com/community/UEFI#SecureBoot](https://help.ubuntu.com/community/UEFI#SecureBoot)

The only other thing I can think to mention is that if you're installing Ubuntu on the same drive as Windows be sure to shrink the main Windows partition using only Windows own tools; Windows Admin Tools > Computer Management > Storage > Disk Management + right click main windows partition + select shrink. It's just safer to resize Windows with it's own tools :)

---

### Post by starbase1 on 2017-03-21
That's extremely helpful, I'll read up and plan on giving it a go at the weekend!

Thank You!

---

### Post by RobGoss on 2017-03-21
Have you tried running the live installer see if you can boot it and access the desktop

---

### Post by oldfred on 2017-03-22
I have a Asus Z97 and my manual is very similar and UEFI/BIOS settins also look similar.
I had to change many UEFI settings. 
Main one was Secure boot which Asus calls "Windows" or "Other". And find print says use "Other" for Windows 7 as it does not support Secure boot.
And to get it to boot flash drive in UEFI mode, I had to use UEFI only. The UEFI or CSM only booted in CSM/BIOS mode.

 Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
I also turned off fast boot (different than Windows fast start up) while installing. And reset to 3 sec delay on warm boot and full start up on cold boot.

---

