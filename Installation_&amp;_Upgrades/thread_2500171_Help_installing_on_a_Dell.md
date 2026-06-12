---
title: "Help installing on a Dell"
date: 2024-08-24
forum: Installation &amp; Upgrades
---

### Post by sports fan Matt on 2024-08-24
So I have my brand new laptop and it’s running Windows 10, unfortunately. I would like to be able to at least in the future on Windows 10 goes away. Be able  to throw Linux on it. When I change the boot order it boots directly into windows. Any ideas? It’s a Dell

---

### Post by grahammechanical on 2024-08-24
I am not clear about what you are doing or not doing.

What are you trying to change the boot order to? Have you installed a distribution of Linux on that machine? Are you trying to boot a USB memory stick with a bootable Linux ISO image on it?

This might help

[https://www.dell.com/community/en/conversations/inspiron/bios-setting-to-boot-usb-uefi-stick/647f7e3ff4ccf8a8decb1e2a](https://www.dell.com/community/en/conversations/inspiron/bios-setting-to-boot-usb-uefi-stick/647f7e3ff4ccf8a8decb1e2a)

I notice that the USB stick should be FAT32 formatted. I am not sure if that is accurate. A Ubuntu ISO image burned to a USB stick would be compliant with ISO9660 standards.

I also note that the USB stick should be in the USB port as the machine boots and you press F12 to enter the UEFI settings utility. I am not familiar with Dell systems, so that might be true.

What are you using to create the Linux USB install memory stick?

Regards

---

### Post by sports fan Matt on 2024-08-24
I’m going to dual boot until
W10 ends with Ubuntu. I can’t figure out how to change the boot order in Dell. I set it to first boot and it boots into windows

---

### Post by sports fan Matt on 2024-08-24
I think i figured it out. F 12

---

### Post by sports fan Matt on 2024-08-24
So when I hit F2 or F12, I can access the bios,but can't access the Ventoy USB even if I change the boot order (secure boot is disabled..Ideas?

My system: Device name	DESKTOP-5FHUVCF
Processor	Intel(R) Core(TM) i7-5600U CPU @ 2.60GHz   2.60 GHz
Installed RAM	16.0 GB (15.9 GB usable)
Device ID	5754A2D4-0F61-4721-A274-8D2459448343
Product ID	00330-50000-00000-AAOEM
System type	64-bit operating system, x64-based processor
Pen and touch	No pen or touch input is available for this display

---

### Post by sports fan Matt on 2024-08-24
> **grahammechanical said:**
> I am not clear about what you are doing or not doing.

What are you trying to change the boot order to? Have you installed a distribution of Linux on that machine? Are you trying to boot a USB memory stick with a bootable Linux ISO image on it?

This might help

[https://www.dell.com/community/en/conversations/inspiron/bios-setting-to-boot-usb-uefi-stick/647f7e3ff4ccf8a8decb1e2a](https://www.dell.com/community/en/conversations/inspiron/bios-setting-to-boot-usb-uefi-stick/647f7e3ff4ccf8a8decb1e2a)

I notice that the USB stick should be FAT32 formatted. I am not sure if that is accurate. A Ubuntu ISO image burned to a USB stick would be compliant with ISO9660 standards.

I also note that the USB stick should be in the USB port as the machine boots and you press F12 to enter the UEFI settings utility. I am not familiar with Dell systems, so that might be true.

What are you using to create the Linux USB install memory stick? 

Regards

Ventoy.

---

### Post by Rubi1200 on 2024-08-24
Have you tried with a different USB stick? Still not recognized?

Perhaps try using Rufus to write to the USB but instead of recommended mode, choose to write to the stick using dd.

Then go to BIOS boot order and see if the stick is recognized.

---

### Post by sports fan Matt on 2024-08-24
When I boot into the BIOS, it does recognize the USB drive.  , I just cannot boot from it, boots straight into Windows.

---

### Post by Adam_GUI on 2024-08-24
How did you go about creating the USB stick?
[Ubuntu Tutorial, including creating from a Windows or MacOS Host here.]("https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview")
Let's use the Ubuntu tutorial and make sure you've followed all the steps.

Be as Verbose as possible as to what you did.  Because, things seem rather unclear, from the thread so far.

---

### Post by sports fan Matt on 2024-08-24
I created it with Ventoy but now I overrode that install with Rufus.  I will try to boot into the USB

---

### Post by sports fan Matt on 2024-08-24
That indeed worked I’m surprised it wouldn’t boot the first time ~, I had to re-create the image from Rufus apparently

---

### Post by Rubi1200 on 2024-08-25
All good now?

If yes, please mark this thread as Solved.

Thanks.

---

### Post by sports fan Matt on 2024-08-25
Yes and I will.

---

