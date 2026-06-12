---
title: "Issues with boot selection, most likely UEFI issue"
date: 2013-10-10
forum: Installation &amp; Upgrades
---

### Post by HonorableFool on 2013-10-10
Hello and thank you for your interest in my problem I will try to be as brief as I can.

What I am attempting is to make Ubuntu my prime or at least dual boot operating system with My windows 7 (Legal) but have had no progress installing Ubuntu, the Versions Ive tried are as follows, 12.04.03: 32bit / 64bit / and alternative - 13.04: 32bit / 64bit  attempted on Physycal Rewritable DVD's, Bootable USB drives, and Mounted ISO images. The Hash downloads were a perfect match with md5sum and the USB Drive installed perfectly on my roomates ACER. Also The Mounted ISO 12.04.03 is installed Via VM through Oracle Virtual Box currently.

System specs: HP P7-1235 (Known to have a version of UEFI) OEM Windows 7 home prem. SP1

AMD A8-5500 APU
MSI MS-7778 (Jasmine)
8GB DDR3 Dual Ram
1TB 7200 RPM SATA
BIOS: AMI v7.07 Dated 04/20/2012 (according to CPU-Z)

I also have a GeForce GT 640 Graphics card, but since I reinstalled windows its not recognized at the moment.

Process:
Attempting to install Ubuntu with the Traditional Method, the process would always "Install" just fine while in windows os then once it reboots I would get the error screen:

Windows failed to start. A Recent hardware or suggested change might be the cause. To fix the Problem:

1. Insert your Windows instillation disc and restart your computer.

2. Choose your language settings and click "Next."

3. Click "Repair your computer."

If you don't have this disc, contact your system administrator or computer manufacturer for assistance.



Highlighted it would say Windows7 (which if selected and entered, would boot windows normally) and at least 1 Ubuntu, more if I had ISO mount+Disk or USB, when selected give this response

             File:   \Ubuntu\winboot\wubildr.mbr

             Status: 0xc0000098

             Info: The selected entry could not be loaded because the application is missing or corrupt.

After several failures of this, I, not knowing anything about UEFI or that it was a factor on my machine, Reinstalled Windows7 x64 using a mounted ISO image. After which I installed Ubuntu 12.04.03 x32 via Oracle VM.

After searching for BIOS downloads for my comp and finding none, and learning about UEFI. I tried to Disable a secure boot or revert my UEFI to legacy within the BIOS, However on startup, after bypassing the previous screen using F10.. I am presented with:

     Edit boot options for: Windows7

Path:   \Windows\system32\winload.efi


Partition: {b5e7c45b-ef02-4c90-877c-ece156d30c9a}
Hard Disk: {56c9cc4b-f2a3-4507-8bd9-4de5b9429320}

[/NOEXECUTE=OPTIN_


  ........... Now im too reluctant to attempt anything further on my own, please advise, anything helps :D  "Help me Obi wan kanobi... Your my only hope!"

---

### Post by joelgsf on 2013-10-12
Have a look at [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI").

---

