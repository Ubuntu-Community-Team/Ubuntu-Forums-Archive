---
title: "Installing Ubuntu Mate on SSD. Seek guidance to best practice."
date: 2018-11-14
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2018-11-14
Now that the HDD issues in this process are mostly sorted (with thanks to all who coached me), it is now time to move to the next topic and to get Ubuntu Mate 18.04 installed on the SSD.

I am going to install UM (from USB) onto an 2 year old new Toshiba 120Gb SSD (Q300 SATA III - 3 bit per cell) as a dual boot with Win 10 (UEFI) on the HDD. It has been two years since I last did an UM install, and two things have happened: (1) my memory of the experience has dimmed, and (2) technology has moved along smartly.

OldFred has been kindly giving me multiple links that tell (generally) WHAT one needs to do, that I have been trying to read and understand, and am getting more and more confused by. At this point I need to reach out to try to find someone who can tell me HOW to do this (as opposed to WHAT needs to be done). My apology for giving up (after 6 days) on trying to puzzle it out, but I am exhausted at this point and about ready to chuck it and go back to Windows.

To recap, Win 10 seems to be properly installed on the 1T HDD (UEFI), with additional partitions for Win data (NTFS), and linux data (not yet formatted)

BIOS setup shows that the computer is in UEFI mode
I have turned off Secure Boot
I have turned off Fast Startup but cannot find where/how to turn off Fast Boot. (Guidance will be appreciated if needs to be off.)

Here are notes I made from within BIOS setup which may/may not be important (If anything needs changing, please advise)
All these are enabled:
Intel Hyper-Threading Technology
Intel SpeedStep Tech.
CPU XD Support
Mullti Core Support
Intel Turbo Boot Tech 

This one is disabled:
Limit CPU Value

SATA mode is AHCI
Boot mode UEFI

Does anyone see anything above that needs to be addressed before starting the install, or not see something that needs addressing?

Your patience and guidance greatly appreciated.

---

### Post by mitesh.agrwl on 2018-11-14
> I have turned off Fast Startup but cannot find where/how to turn off Fast Boot

According to Google search results both are same from Windows 10 perspective. 

From BIOS/UEFI settings panel, change the boot order, select CD-ROM or USB, whichever is going to be used for installation, as first boot device. In general I like to keep HDD as last option in boot priority.

While installing iso on USB to make live USB/CD, [make ensure it support UEFI boot mode]("https://www.lifewire.com/create-uefi-bootable-linux-mint-usb-2202084").

---

### Post by Odyssey1942 on 2018-11-14
This came up pretty high in my Google results:

[http://www.tomshardware.com/answers/id-3366685/fast-boot-fast-startup.html]("http://www.tomshardware.com/answers/id-3366685/fast-boot-fast-startup.html")

But I still can't find it in the BIOS.

Thanks for the tip on ensuring that the USB installer supports UEFI

And I think I have reached the "Learning" status. :P

Anyone see anything else?

---

### Post by mitesh.agrwl on 2018-11-14
> his came up pretty high in my Google results:

[http://www.tomshardware.com/answers/...t-startup.html]("http://www.tomshardware.com/answers/id-3366685/fast-boot-fast-startup.html")

But I still can't find it in the BIOS.


You can confirm this by via BIOS/UEFI version. In Windows,
To find the BIOS or UEFI version in Windows 10, do the following.
          Open an elevated command prompt.
          Type the following command: **wmic** 
              get BIOS/UEFI name, version, serial number.

[LIST] 
[/LIST]
From the version check whether it has this feature, if yes, how to set it.

Alternatively, you can visit the support centre of the motherboard/laptop vendor to check the same.

---

### Post by oldfred on 2018-11-14
Attached is my Asus boot screen which shows fast boot setting.
But every system is a bit different, even though UEFI is a standard.

---

