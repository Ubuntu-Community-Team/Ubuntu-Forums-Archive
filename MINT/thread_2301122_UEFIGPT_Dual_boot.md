---
title: "UEFI/GPT Dual boot"
date: 2015-10-30
forum: MINT
---

### Post by Blaise170 on 2015-10-30
As many others have experienced, dual booting Linux alongside Windows is a pain. I've searched forum after forum and tried fix after fix but I still can't get anything working. I'm using Windows 8.1 in UEFI mode. I have three disks: sda (Windows 256GB SSD), sdb (Linux 32GB SSD), and sda3 (storage only). I've tried using boot repair to no avail. I used boot repair's built in paste function and here are the results for my system.

[http://paste2.org/s3vf1wzY](http://paste2.org/s3vf1wzY)

---

### Post by grahammechanical on 2015-10-30
I do not give support to Linux Mint but I will tell you this. I think that Windows is installed in BIOS/legacy/compatibility mode and Linux Mint is installed In EFI mode. And that is where the pain begins.

> 
[LIST]
[*]if the other systems (Windows Vista/7/8, GNU/Linux...) of your  computer are installed in UEFI mode, then you must install Ubuntu in  UEFI mode too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And as boot repair says: "no-win-efi"

Regards.

---

### Post by yancek on 2015-10-31
> I'm using Windows 8.1 in UEFI mode.

Your boot repair output indicates windows is installed MBR.  If it was UEFI, you would have an EFI partition and windows files on that partition and there are none.  You have windows on a separate disk so you might be able to boot by selecting the disk from BIOS during boot.  Since you have windows code in the MBR of both the windows and Linux Mint disk, you would have to configure your windows bootloader to boot Linux.  That or reFind which you have.  I'm not sure why you would have windows code in the MBR of the disk on which you have Mint installed as there are no windows partitions there.  Also, if you are using UEFI on a disk, you should not have any code in the MBR.

The link posted above should explain.

---

### Post by howefield on 2015-10-31
Thread moved to the "*MINT*" forum.

---

### Post by Blaise170 on 2015-10-31
Ah I see. I thought for sure than I had UEFI enabled when I installed Win8, but sure enough changing the bootloader to legacy mode allowed Win8 to come right up. Is there an easy way to remove the UEFI GRUB loader and install the legacy loader or should I just do a reinstall to make life simpler? It's only been installed for a couple of days now so I won't lose much.

P.S. Sorry that Mint isn't really supported here, but it was more of a general question about the boot so I didn't think it would make a huge difference.

---

