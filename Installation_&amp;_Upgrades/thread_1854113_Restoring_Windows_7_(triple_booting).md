---
title: "Restoring Windows 7 (triple booting)"
date: 2011-10-03
forum: Installation &amp; Upgrades
---

### Post by Swazilli on 2011-10-03
Hey Ubuntu forum. I've been having this issue for the past several days and I can't seem to solve it. Here is my situation in detail:

I used to have a hackintosh. There was one hard drive and 3 partitions. 1- the efi/bootloader (chameleon) 2-windows 7 and 3 Mac os x

I then decided to install Ubuntu. So ishrink my Mac OS X partition (GUID partition table) and install Ubuntu on the newly available space. Unfortunately I installed Grub (v1.99) over my bootloader. Now I can not boot Windows 7 or Mac OS X. Ubuntu works fine. So I did some googling and it turns out my MBR is overwritten by grub and I should fix that.
 

 So I installed Lilo and ran the command to fix MBR. Now grub does not work. I get an error: No active partition found. I can not boot into anything. Luckily when I made my hackintosh installation, I made an external disk with chameleon on it (my bootloader). So I booted off that and can access my Mac OS X and my Ubuntu installation. So I booted into my Mac OS X and I thought, maybe I should re-install my bootloader. So I reinstalled chameleon. Now when I restart I get an “No Boot Signature in partition”
 

 I then used my external disc to boot back to Ubuntu. At this point in time, I can use my external dsic to boot to Ubuntu and Mac OS X. When I try to boot into Windows 7 I get a can't find /Boot/BCD error. I then downloaded UltimateBoot CD and tried running a combination of MBR fixing utilities (MBR Wizard and SuperGrub/2). Since I didn't know what any of the options mean. I did not fix anything. Now when I restart my computer I just get a blinking cursor.
 

 

 So here is where I am at now. I can only boot into an OS using my external hard disk. I can only boot into Ubuntu/Mac OS X. When I try to boot to Windows 7 I get a “Boot/BCD” error.
 

 Here is what I tried:
 I tried using my Windows 7 install disk to repair my installation. It did not work. It tells me that it is not compatible with my version of Windows. I tried both my disc (64 bit) and a friends disc (32 bit). No luck. I might know the explanation for this. If I try to install Windows 7 it tells me that all my partitions are “ext4” (even the Mac one). However when I view it in Ubuntu Disk Manager, I get the proper partitions (Hfs+/NTFS). The partition types states: “Linux Basic Data Partition”. Even for Windows 7. Here is a screenshot:
 

[http://i.imgur.com/YyLjW.png](http://i.imgur.com/YyLjW.png)
 

 EFI is /dev/sda1, Mac is /dev/sda2, Windows is /dev/sda3 and 60 GB is /dev/sda4
 

 I am really at a loss of what to do. I can see all my files in the windows partition, so I am considering just backing them up and then reinstalling. But that is a last resort. Is there anything I can do?

---

