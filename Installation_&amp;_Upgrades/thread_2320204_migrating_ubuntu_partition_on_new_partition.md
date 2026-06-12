---
title: "migrating ubuntu partition on new partition"
date: 2016-04-11
forum: Installation &amp; Upgrades
---

### Post by marscar on 2016-04-11
I have Ubuntu 14.04 installed on a partition of my old HDD alongside win7 with grub2 boot-loader.
I want to re install Ubuntu only on a new HDD (and new laptop) alongside win 10 and don't care about data on win7.
So far I was able to run Ubuntu from the external HDD on my new laptop, I installed the new drivers, disabled secure boot, ... Bottom line it Ubuntu runs smoothly from the old HDD mounted on the new laptop through USB/SATA port. 
Now, how  do I install it on the new HDD and use win10 boot-loader?
Thanks, Marcello

---

### Post by grahammechanical on 2016-04-11
> use win10 boot-loader?

When did Microsoft start providing a boot loader that recognised Linux operating systems and loaded them? Here is the situation.

With Windows 8 & upwards whatever mode Windows is installed in Linux has to be installed in the same mode. Windows 10 would have been installed in EFI mode and as Windows 7 would not have been installed in EFI mode neither would Ubuntu have been.

A new install of Ubuntu on to that hard drive would require Ubuntu to be installed in EFI mode the same as Windows 10. A new install of Ubuntu would use Grub as the boot loader rather than  the Windows 10 boot loader. It has to do that otherwise there would not be a dual boot. Windows boot loaders do not let Linux dual boot with Windows.

Windows 10 would be on a GPT partitioned drive with efi boot files in an efi boot partition. A fresh install of Ubuntu would put Ubuntu efi boot files in the same efi boot partition alongside & coexisting with the Windows 10 efi boot files. Which should mean we can load either Ubuntu or Windows 10 from the Grub menu or load either from the UEFI settings utility.

The disk with Windows 7 & Ubuntu on it would have MBR partitioning. There would be no efi boot partition & no efi boot files. I see mega issues with what you want to do. 

Regards

---

### Post by sudodus on 2016-04-11
Ubuntu can boot from an MBR (MSDOS) partitioned drive in UEFI mode. You have to add an EFI partition and install the grub-efi bootloader: Not easy but possible. So if you have two drives, that could be a solution. Ubuntu can run from a USB drive (HDD, SSD or pendrive) or eSATA drive, if you have an eSATA port.

If you accept switching between UEFI and BIOS mode to run Windows and Ubuntu, it will be straight-forward, but that is not convenient in the long run.

-o-

But if you want your old Ubuntu and Windows 10 on the same drive, it will probably be very difficult to get everything right.

I would recommend a ***new installation*** of Ubuntu instead of trying to convert it.

---

### Post by marscar on 2016-04-11
Thank you all,
I appreciated your prompt reply.
Marcello

---

### Post by marscar on 2016-04-11
Thank you all,
I appreciated your prompt reply. Looks like I have not much choice but a new installation. I suppose I have to re-download the most updated version of Ubuntu 14.04 which will eventually and hopefully support UEFI.
Please advise if that is possible. Thanks
Marcello

---

### Post by sudodus on 2016-04-11
The version 14.04.4 is the newest point version of the 14.04 LTS. Maybe you should get the 64-bit iso file **ubuntu-14.04.4-desktop-amd64.iso**, maybe an earlier version, if the computer is old, maybe a newer version if the computer model is brand new, possibly even the next version Xenial Xerus (which will be released as 16.04 LTS before the end of this month).

Before selecting version and deciding if you should get standard Ubuntu or some flavour with lighter desktop environment, please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by marscar on 2016-04-11
@ sudodus
I would rather install 14.04 version for I guess it would be consistent with the sw I developed and I will migrate to the new OS. Particularly I used Python 2.7 for developing quite an  amount of applications.
I read some forums in regard and I understand the most common practice is to copy /home to the new HDD and use dpkg for listing all installed packages and auto reinstall everything. Ifinstalling 16.04 does not change much my plans sure I will install it.
My system info:
OS Name	Microsoft Windows 10 Home
Version	10.0.10586 Build 10586
Other OS Description 	Not Available
OS Manufacturer	Microsoft Corporation
System Name	DESKTOP-M6PTLN2
System Manufacturer	LENOVO
System Model	80R4
System Type	x64-based PC
System SKU	LENOVO_MT_80R4_BU_idea_FM_Flex 3-1580
Processor	Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz, 2592 Mhz, 2 Core(s), 4 Logical Processor(s)
BIOS Version/Date	LENOVO D3CN27WW, 10/28/2015
SMBIOS Version	2.8
Embedded Controller Version	1.23
BIOS Mode	UEFI
BaseBoard Manufacturer	LENOVO
BaseBoard Model	Not Available
BaseBoard Name	Base Board
Platform Role	Mobile
Secure Boot State	Off
PCR7 Configuration	Elevation Required to View
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "10.0.10586.0"
User Name	DESKTOP-M6PTLN2\MScar
Time Zone	Eastern Daylight Time
Installed Physical Memory (RAM)	7.85 GB
Total Physical Memory	7.85 GB
Available Physical Memory	2.22 GB
Total Virtual Memory	14.4 GB
Available Virtual Memory	8.12 GB
Page File Space	6.50 GB
Page File	C:\pagefile.sys
Hyper-V - VM Monitor Mode Extensions	Yes
Hyper-V - Second Level Address Translation Extensions	Yes
Hyper-V - Virtualization Enabled in Firmware	No
Hyper-V - Data Execution Protection	Yes

Thank you,
-M

---

### Post by sudodus on 2016-04-12
If this is the computer:

[http://www.cnet.com/products/lenovo-flex-3-1580-80r4-15-6-core-i7-6500u-8-gb-ram-1-tb-hdd/specs/](http://www.cnet.com/products/lenovo-flex-3-1580-80r4-15-6-core-i7-6500u-8-gb-ram-1-tb-hdd/specs/)

I think it should work well with any operating system. It is a good idea to try with the 64-bit iso file **ubuntu-14.04.4-desktop-amd64.iso** :-)

But if the hardware is too new for 14.04 LTS, you will have better luck with the newest possible Ubuntu version, Xenial Xerus (which will be released as 16.04 LTS before the end of this month).

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by marscar on 2016-04-12
@sudosud,
that is the correct machine. I will go with 14.04 desktop. I am aware of the missing drivers and I already tweaked my current version to run on this machine. I will post updates anyway.
-M

---

### Post by sudodus on 2016-04-12
Good luck :-)

---

### Post by marscar on 2016-04-12
worked like a charm! Drivers were updated, worked out of the box. I did not copy all my old files and settings, though. I thinkit's a better idea to install packages on the go. Az lot of stuff might not even be useful anymore

---

### Post by sudodus on 2016-04-13
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

