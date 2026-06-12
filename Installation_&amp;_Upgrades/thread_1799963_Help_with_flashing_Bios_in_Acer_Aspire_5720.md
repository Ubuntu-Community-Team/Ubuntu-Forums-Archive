---
title: "Help with flashing Bios in Acer Aspire 5720"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by pramsay13 on 2011-07-08
I'm needing some help flashing the BIOS in my Acer Aspire 5720z. Issue is that fan won't switch on since update to Natty and so laptop overheats and shuts down. I know the risks and I'm pretty sure these issues are BIOS related so I am wanting to do it.
The howtos I have read and the other threads aren't quite enough so any direct help would be great.
The file from Acer is  BIOS_v1.45.exe file and can be further extracted. Files are InsydeFlash.exe, iscflash.dll, iscflash.sys, platform.ini, CL50145A.fd, iscflashx64.sys.
I have tried a few different methods and the closest I have come is creating a Dos Boot Disc with .exe file on it (although during creating it said there was no more space for .exe file but seemed to work ok)
I can then boot into dos and find .exe file but it says file cannot be executed in DOS.
Any ideas, preferably with step by step instructions?
Cheers

---

### Post by dino99 on 2011-07-08
follow their instructions carefully:

[http://support.acer-euro.com/drivers/notebook/as_5720.html](http://support.acer-euro.com/drivers/notebook/as_5720.html)

download the guide at bottom of that link

---

### Post by MAFoElffen on 2011-07-08
> **pramsay13 said:**
> I'm needing some help flashing the BIOS in my Acer Aspire 5720z. Issue is that fan won't switch on since update to Natty and so laptop overheats and shuts down. I know the risks and I'm pretty sure these issues are BIOS related so I am wanting to do it.
The howtos I have read and the other threads aren't quite enough so any direct help would be great.
The file from Acer is  BIOS_v1.45.exe file and can be further extracted. Files are InsydeFlash.exe, iscflash.dll, iscflash.sys, platform.ini, CL50145A.fd, iscflashx64.sys.
I have tried a few different methods and the closest I have come is creating a Dos Boot Disc with .exe file on it (although during creating it said there was no more space for .exe file but seemed to work ok)
I can then boot into dos and find .exe file but it says file cannot be executed in DOS.
Any ideas, preferably with step by step instructions?
Cheers
One thing your might try beforehand is to add 
```
[FONT=monospace]
[/FONT]acpi_osi=Linux

```
to the kernel boot line as a kms switch.  This has been correcting a lot of apci problems in laptops with natty... especially where the fans are not coming on.

Look at Post #1 of this sticky in the laptop workaround section...
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") 			
It has instructions there in that first post on how to add it temporarily to test it and if it works, how to make it permanent.

---

### Post by pramsay13 on 2011-07-10
Thanks MAF but I already have that line in the grub loader.
Thanks Dino, I'll have a look at that page in detail and let you know how I get on. It's too late to try something risky tonight!

---

### Post by pramsay13 on 2011-07-12
I've created a DOS disc with IF50.BAT on it, which is how to flash the BIOS according to the v1.42 README file. Unfortunately I am still getting an error message when I try to launch this at the DOS prompt. 
Any ideas?

---

