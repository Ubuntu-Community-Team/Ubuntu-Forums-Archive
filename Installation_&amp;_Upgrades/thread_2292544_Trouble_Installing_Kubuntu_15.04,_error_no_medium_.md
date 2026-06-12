---
title: "Trouble Installing Kubuntu 15.04, error no medium found &amp; [35.844347],[35.833.454]..."
date: 2015-08-29
forum: Installation &amp; Upgrades
---

### Post by o-own-you-jelly on 2015-08-29
[COLOR=#000000][FONT=Arial]SITUATION:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I am trying to install Kubuntu 15.04 on my main desktop computer but keep encountering errors when I try and install.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]MY INFO:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I am a beginner to linux / ubuntu. I am fairly knowledgeable with basic terminal commands, and have a vast experience with PC&#8217;s as a whole. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]MY COMPUTER INFO:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I got this info using Piriform Speccy v 1.28.709(64-bit)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OS - Windows 8 64-bit Version 6.2 (Build 9200) [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]CPU - Intel Core i5-3570K @ 3.4Ghz [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]RAM - 16Gb Dual-channel DDR3 @ 666Mhz (9-9-9-24)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Motherboard - ASROCK Z77 Extreme 4 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Integrated Graphics - Intel HD Graphics 4000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Discrete Graphics - NVIDIA GeForce GTX 660[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Storage - 1863GB (2TB) Seagate ST2000DM001-9YN164 ATA Device (Sata) / I also have an SSD connected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Optical Drive - Optiarc DVD RW AD-7280S ATA  Device[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Network - D-Link DWA-556 Xtreme N PCIe Desktop Adapter[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Additional Info - [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I chose to disconnect my mouse, my speakers, my headphones, and my touchpad to try and minimize unneeded peripheral errors.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]**Any additional info will be provided on request. short instructions on how to obtain them would be appreciated. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]MY ERROR INFO:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]RUN 1. Optical Drive in mode SATA 
[/FONT][/COLOR]```

[COLOR=#000000][FONT=Arial][3.401578] ACPI PCC prob failed[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]starting version 219[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]error: /dev/sdc: no medium found[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]error: /dev/sdd: no medium found[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]error: /dev/sde: no medium found[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]error: /dev/sdf: no medium found[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]error: /dev/sdc: no medium found[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]error: /dev/sdd: no medium found[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]error: /dev/sde: no medium found[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]error: /dev/sdf: no medium found[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][35.844347] ata5.00: exception Emask 0x52 SAct 0x0 Serr 0xffffffff action 0xe frozen[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][35.833454] ata5: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt PHYRdyChg PHYInt CommWake 10BB Dispar BadCRC Handshk linkSeq TrStaTrns UnrecFIS DevExch}[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][35.844361] ata.5.00 failed command: IDENTIFY PACKET DEVICE[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][35.844365] ata5.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 4 pio 512 in[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][35/844365] res 40/00:01:00:00:00/00:00:00:00:00/00  Emask 0x56 (ATA bus error)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][35.844371] ata5.00: status: { DRDY }
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Arial]RUN 2. Optical Drive in mode UEFI[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SAME EXACT RESULTS AS ABOVE WITH EXCEPTION OF ERROR: /DEV/SD*: NO MEDIUM FOUND[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The order in which SD* is different every run I have done so far.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]ADDITIONAL INFO:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I do not know if this helps, but I have noted a few things in research of finding a solution:[/FONT][/COLOR]

[LIST]
[*]I have my storage configuration set to IDE, instead of AHCI; This has reduced some errors.
[*]I have switched from attempting to install with USB to DVD. USB kept showing issues with &#8220;write through&#8221; cache, switching over also reduced errors.
[*]How did you install kubuntu? - I installed it from there direct link at &#8220;[COLOR=#1155CC]_[http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)_[/COLOR]&#8221;
[*]Did you check the SHA256? - I used &#8220;[[COLOR=#1155CC]_Raymond&#8217;s MD5 & SHA Checksum Utility_[/COLOR]]("https://raylin.wordpress.com/downloads/md5-sha-1-checksum-utility/")&#8221; and it matched the checksum given to me on the kubuntu website. I checked the amd64 SHA since I installed 64-bit
[*]Which tool did you use to make a DVD / USB Bootable with kubuntu? - I used &#8220;[[COLOR=#1155CC]_ImgBurn_[/COLOR]]("http://www.imgburn.com/")&#8221;. I turned &#8216;verify&#8217; off and set the write speed to x2.5
[*]does it run live? - It does not run live.
[/LIST]

[COLOR=#000000][FONT=Arial]WHAT I EXPECT AS A SOLUTION:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I expect to find a solution to my boot error; so that I can successfully install linux as my main operating system. I do NOT plan on dual booting with my current OS
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]WHAT I EXPECT AS PROBLEMS:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I expect that I may have a hardware problem; such incompatibility or that I may have a feature turned on, that should be turned off.

-I  Highly Appreciate any and all help on solving this issue. I plan on changing my OS to linux as a long-term goal, I do not plan on giving up. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-08-29
Welcome. If it does not run live then go no further and forget looking for other problems for now. You very well don't have any and the things you've unplugged wouldn't be the issue (very doubtful). [Download the torrent file]("http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/kubuntu/releases/14.04/release/") and get the ISO via a torrent (start with 14.04 LTS which is stable and supported until 2019). Use Unetbootin or Universal USB installer to create a bootable USB. 

*** If you have Win installed, you need to boot into it and switch off hibernate and faststart and make sure secure boot is switched off in the BIOS. If Win is in hibernate it may cause similar issues to what you're getting as Ubuntu can't access the hard drive if Win 'owns' it in hibernate. The disk is 'closed' which is why you can't access any partitions.

UNetbootin:
unetbootin.sourceforge.net

Universal USB Installer:
[www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Boot from the USB and if you can't 'Try Kubuntu' live then you have an issue that may have little to do with your hardware and more to do with the USB or the way you've created it (or the disk).

Bottom line: if you can't run Kubuntu live, don't go further. We need to work out why. Report any and all errors you get when attempting to run live (not install). That will probably give more clues.

PS: Please use code tags for output. See the last link in my signature. Thanks.

---

### Post by SeijiSensei on 2015-08-29
Do you have another machine that you can try the DVD in?  Does that work if you run "Try Kubuntu"?

---

### Post by o-own-you-jelly on 2015-08-29
[SIZE=3][FONT=arial][COLOR=#ff0000]@BuckyBall[/COLOR]
I downloaded the torrent from kubuntus's website; And I used Universal
USB Installer.
[/FONT]
[FONT=arial]new problem[/FONT]
[FONT=arial]```

[5.281637] sd 6:0:0:0 [sdc] No Caching mode page found
[5.281649] sd 6:0:0:0 [sdc] Assuming drive cache: write through

```
&#8203;Same as before
[/FONT]```
[35.896300] ata5.00: exception Emask 0x52 SAct 0x0 Serr 0xffffffff action 0xe frozen
[35.896309] ata5: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt PHYRdyChg PHYInt CommWake 10BB Dispar BadCRC Handshk linkSeq TrStaTrns UnrecFIS DevExch}
[35.896315] ata.5.00 failed command: IDENTIFY PACKET DEVICE
[35.896320] ata5.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 22 pio 512 in
[35/896320] res 40/00:01:00:00:00/00:00:00:00:00/00  Emask 0x56 (ATA bus error)
[35.896325] ata5.00: status: { DRDY }


```

[FONT=arial]I also attempted to see if I had any hibernation, or faststart, or secure boot, And I am pretty sure they are all off. I need to check my bios info because I did not see a secure boot option to turn off, but If I do not mention this in my next post just assume I have resolved all these issues already.
[/FONT][/SIZE][SIZE=4][SIZE=3][FONT=arial]
[COLOR=#ff0000]@SeijiSensei[/COLOR]
Yes I tried running it on a near by desktop, and it ran successfully.[/FONT]
[FONT=arial]This was with Kubuntu 14.04 (LTS) via torrent witch I obtained from kubuntu's website and on USB using Universal USB Installer as suggested by [/FONT][COLOR=#b22222][FONT=arial]Bucky Ball[/FONT][/COLOR][/SIZE][FONT=arial]
[/FONT][/SIZE]

---

### Post by Bucky Ball on 2015-08-30
Please use default font and point size and attach large pics by 'Go Advanced' and using the paperclip icon. Thanks.

---

### Post by oldfred on 2015-08-30
With Asrock do not use an asmedia ports, even for DVD and not using DVD.

 Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

Also with nVidia you usually need to use nomodeset.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If booting with internal Intel video chip, you may need different settings than nomodeset.

---

### Post by o-own-you-jelly on 2015-08-30
Thank you for everyone's I solved the issue by updating my bios on Asrock and this gave me the option to turn off secure boot.

---

