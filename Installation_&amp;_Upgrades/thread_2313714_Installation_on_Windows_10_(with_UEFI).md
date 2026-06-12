---
title: "Installation on Windows 10 (with UEFI)"
date: 2016-02-15
forum: Installation &amp; Upgrades
---

### Post by Macamba on 2016-02-15
I previously installed Ubuntu on systems with Windows XP. This system uses BIOS. Now I have a Windows 10 system, and I noticed it did not want to boot from (the Ubuntu installation) DVD. I now found out booting is prohibited by UEFI. How can I turn this UEFI off?

Looking at the Startup Settings screen of my boot loader (?) I see:
```
1) Enable debugging
2) Enable boot logging
3) Enable low-resolution video
4) Enable Safe Mode
5) Enable Safe Mode with Networking
6) Enable Safe Mode with Command Prompt
7) Disable drive signature enforcement
8) Disable early launch anti-malware protection
9) Disable automatic restart after failure
```

And on the next page
```
1) Launch recovery environment
```

And to get into this screen I pressed Shift while clicking the reboot menu item in the Power menu

---

### Post by sudodus on 2016-02-15
Please specify your computer

- Brand name and model (this is particularly important because the UEFI systems are often tweaked by the manufacturers)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Knowing this about your computer helps us help you :-)

---

### Post by Macamba on 2016-02-15
It is an "[ADMI VS-92 White GAMING PC]("http://www.amazon.co.uk/gp/product/B00DRG0HNY?psc=1&redirect=true&ref_=oh_aui_detailpage_o02_s00")" computer

CPU: --------------------- FX-4350 Quad Core 4.20GHz Processor
RAM (size): ----------- 16GB DDR3 RAM Memory
Graphics chip/card:- AMD Radeon R7 240 2GB Graphics Card
wifi chip/card: -------- None (?, check link). I am connected to my WiFi router by cabel

---

### Post by sudodus on 2016-02-15
I noticed that the computer has a Gigabyte motherboard. Maybe the following post by *oldfred* will help you:

[Re: Installation breaks on creating partitions: IOMMU](http://ubuntuforums.org/showthread.php?t=2313235&p=13438455#post13438455)

---

### Post by Macamba on 2016-02-16
At the moment I know how to come into the CMOS Setup Utility (press Del during boot). 

The helpdesk of the computer manufacturer advised me to "change the settings in the BIOS so it says other OS and not windows 8/10". I take it the BIOS is the same as the CMOS? In that case I could not find the location where to change the setting from Windows to Other OS. 

**Does anyone know where I can change the OS in the CMOS?**

At the moment I have reshuffled the boot order in the Advanced BIOS features to:
First boot device:  CDROM
Second boot device: Hard Disk
Third boot device: USB-HDD

But during start up the CDROM is not accessed. **What do I need to do to get the computer to read the CDROM during boot?**

Edit:
Might it be possible that the "Disable early launch anti-malware protection" is making it impossible for me to install Ubuntu from DVD?

---

### Post by grahammechanical on 2016-02-16
BIOS = Basic Input Output System. It is used by the motherboard as its own little boot system. The settings are stored in a CMOS memory chip = Compatible-Metal-Oxide-Semiconductor. So, BIOS setup utility = CMOS set up utility.

UEFI = Unified Extensible Firmware Interface. It replaces the BIOS/CMOS as a motherboard boot system. And we cannot remove it.

It may be, and without having your motherboard I cannot say for sure, that the option to select an OS other than Windows will only appear in the UEFI utility if the DVD is present in the drive when you open the UEFI utility. And then it may appear as a boot option.

Windows 10 will be installed in what is called EFI mode. This means that the Ubuntu live session (DVD disc/USB memory stick) must also be run in EFI mode so that Ubuntu installs in EFI mode. Otherwise you will end up with a situation where you can only load one OS and not the other without going in & out if the UEFI utility to change the boot order.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by Macamba on 2016-02-16
> **grahammechanical said:**
> This means that the Ubuntu live session (DVD disc/USB memory stick) must also be run in EFI mode so that Ubuntu installs in EFI mode.

And how do I start the Ubuntu live session in EFI mode? Especially when during boot I am not able to boot from DVD?

---

### Post by sudodus on 2016-02-16
Did you find how to change IOMMU settings according to oldfred's post (linked in post #4)?

> Those Gigabyte boards need IOMMU settings changed in UEFI and a boot parameter.

---

### Post by oldfred on 2016-02-16
Every UEFI is different. This screen shot is from Asus.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    Some seem to require CSM on, even though you want to default to UEFI. Others just have UEFI/CSM switch. And you want UEFI.

With my Asus I had many settings to change. 
So you need to review all your UEFI settings.

---

### Post by Macamba on 2016-02-16
> **sudodus said:**
> Did you find how to change IOMMU settings according to oldfred's post (linked in post #4)?

I tried to find the appropriate entry I could use. But no, sadly not.

> **oldfred said:**
> Every UEFI is different. This screen shot is from Asus.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    Some seem to require CSM on, even though you want to default to UEFI. Others just have UEFI/CSM switch. And you want UEFI.

With my Asus I had many settings to change. 
So you need to review all your UEFI settings.

I think that is the problem for me. I do not see a way into UEFI. I read online to enter UEFI (from Windows 10) that I need to SHIFT press Restart from the Power menu. But if I do that I do not get the 'UEFI Firmware Settings' menu in the 'Advanced options' page (see my attachment (I hope)). 

After SHIFT Restart I get 'Choose an Option' --> Troubleshoot --> Advanced options. And instead of seeing the 'UEFI Firmware Settings' option, I get 'Start-up Settings' on that location.

---

### Post by Macamba on 2016-02-16
After feedback from my supplier I got the suggestion to "[select] &#8220;TSSTcorp CDDVDW&#8221; from the boot menu". My new system is now booting from DVD and hopefully my problems will be solved.

---

### Post by sudodus on 2016-02-16
This is an important step forward :-)

---

### Post by Macamba on 2016-02-16
It seems my problems are over. I restarted my system, got a choice offered in a Grub screen, including Windows 10. 

Thanks **sudodus** and **oldfred** for your helping hand.

---

