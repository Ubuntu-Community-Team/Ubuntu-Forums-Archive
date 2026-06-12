---
title: "Got into grub command line when booting with LiveUSB"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by jack980517 on 2013-08-29
Hi evreyone,
My computer is Acer Aspire V5, with Windows 8 pre-installed and UEFI boot support (legacy mode is also supported). The official guide says that Ubuntu supports UEFI boot as well as Secure Boot, so I just wrote the 12.04 LTS LiveCD ISO file into a USB stick and booted from it without adjusting the UEFI firmware settings. But after booting the grub command line appears instead of the LiveCD selection menu, without any error prompts, just like it should boot into the grub command line. Then I tried turning off Secure Boot, but the situation was the same. I know nothing about grub, so I was stuck here and was unable to proceed to install Ubuntu. The official guide doesn't mention my situation at all. Any solutions?

Jack

---

### Post by TheFu on 2013-08-29
Did you install with 12.04.3 (just released a few days ago) or something older?  I doubt that UEFI support was  backported to 12.04.1 or prior releases.  There is a UEFI how-to on the ubuntu site. Read it, follow it, know it.  google "ubuntu UEFI" to find lots of references.

See my signature for **boot-repair** links. Those are on the ubuntu website. Great tool, don't know if it can help or not, but it is worth a try.

---

### Post by grahammechanical on 2013-08-29
I do not doubt that you are getting a command line instead of a live session but it is not Grub. I do not think that Grub is used in running the live session. Please confirm that you have noted these comments

> 
[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([32bit installer does not detect EFI]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[/FONT]
[*=left][FONT=inherit]Use the last version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[/FONT]
[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[/FONT]
[/LIST]


If you downloaded Ubuntu 12.04 within the last few months then you may have 12.04.2. If you downloaded within the last couple of days then you will have 12.04.3. Either image will install Ubuntu on a machine with secure boot enabled and EFI firmware but note the point about setting the firmware to boot the live DVD in EFI mode. There is also this to take note of

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by oldfred on 2013-08-29
With UEFI boot from the installer you do get the grub (black) menu, not the BIOS (purple)  accessibility screen.

And that should boot. But you must turn fast boot off in Windows/UEFI. Some older systems literally were bricked if fast boot not turned off as the only way into UEFI was thru Windows on those systems. (If Windows would not boot for any reason it also became a brick as there was no way to fix it externally).

But Ultrabooks have two additional issues beyond UEFI vs. BIOS boot. 

You have Intel SRT which uses RAID and interferes with install or install of grub. Intel SRT needs to be turned off and RAID meta-data removed from drive. The Intel SRT can be turned on again and it will work.

Ultrabooks also have dual video. If booting with nVidia as default you need the nomodeset boot option on the linux line in grub menu. Use e at grub menu to edit, scroll down to linux line and replace quiet splash with nomodeset.

More details in link in my signature.

 Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

Other Acer

 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

### Post by dchristianbell on 2013-09-22
Same deal here.  Acer Aspire M, 64-bit 13.04, disabled SecureBoot and FastStartup (not sure what fastboot is), booting a LiveCD in UEFI---rather than getting a menu, just got the grub command line.

---

### Post by oldfred on 2013-09-22
You should get grub menu. Are you sure download was correct? Did you verify ISO with md5sum?
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

A few systems have incorrect UEFI/BIOS, vendors may be updating. Have you installed latest UEFI?

And those incorrect one often will install in BIOS mode, and then using Boot-Repair you can convert to UEFI and have it work.

---

### Post by dchristianbell on 2013-09-26
oldfred: 

Thanks.  Your artifacts are strewn across the Web on this issue; while researching this and related issues, your name keeps coming up, be it on SO, here, or in search results.  

As for my issue, it was stupid:  I had installed ubuntu previously, then factory-reset my machine.  The factory reset left one part of my hard drive still named "ubuntu," and it was that that I was booting into, not the LiveCD.  I write this now from ubuntu, so you can tell things worked out in the end.

Thanks!

---

### Post by oldfred on 2013-09-26
Glad you got it working. :)

---

