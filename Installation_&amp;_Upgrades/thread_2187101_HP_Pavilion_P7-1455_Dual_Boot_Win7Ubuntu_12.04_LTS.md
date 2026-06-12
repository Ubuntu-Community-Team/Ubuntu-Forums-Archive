---
title: "HP Pavilion P7-1455 Dual Boot Win7/Ubuntu 12.04 LTS Problems"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by edwinfinch8 on 2013-11-10
Hey everyone,

First of all I'd like to apologize in advance if I'm posting in the wrong category.

To the point:

I've tried installing Ubuntu 64 bit 12.04 LTS (on a CD, not USB) along with Windows 7. The computer came pre-installed with Windows 8, and I had to do some re-working of the BIOS settings for Windows 7 to install. I tried a few days ago to install Ubuntu on the computer but haven't had time to fix it until now. 

Here are some specs so you don't have to go digging:
Motherboard: [COLOR=#333333][FONT=arial]MSI MS-7778 (Jasmine) (This board is UEFI by default)[/FONT][/COLOR]
Processor: [COLOR=#333333][FONT=arial]AMD A10-5700
Ram: 8GB

What are some solutions to this? Even when I get into the Windows boot manager, it doesn't show Ubuntu as an option.

I've also dedicated 500GB of my HDD for Ubuntu.

Thanks!

PS. Here are some photos I've attached with more details:

[/FONT][/COLOR][IMG]http://i.imgur.com/A3AWAGd.jpg[/IMG][IMG]http://i.imgur.com/2KABE0J.jpg[/IMG][IMG]http://i.imgur.com/4ZXKSxX.jpg[/IMG]

---

### Post by ubfan1 on 2013-11-11
Did you convert your disk to msdos partitioning or leave it gpt partitioned?  If you left it gpt, did you create a small (1M?) partition (near the beginning of the disk) with the grub_bios flag?

---

### Post by oldfred on 2013-11-11
Even if BIOS/ with MBR(msdos) partitioning you should use AHCI not IDE. Windows 7 may need drivers installed first before you change.

From terminal in live installer. You did use DVD not CD as CD is not large enough now. Flash drive is usually better/quicker/reuseable.
       sudo parted /dev/sda unit s print

---

