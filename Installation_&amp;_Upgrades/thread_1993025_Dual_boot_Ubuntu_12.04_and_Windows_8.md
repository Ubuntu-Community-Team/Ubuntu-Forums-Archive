---
title: "Dual boot Ubuntu 12.04 and Windows 8"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by waspinator on 2012-06-01
I downloaded [Windows 8 Release Preview]("http://windows.microsoft.com/en-US/windows-8/download") and installed it from scratch on an old computer. It's very smooth and works surprisingly well. Now I want to install Ubuntu 12.04. After booting from a live usb I start the installer, but it doesn't show me any partitions. It just shows a blank 149GB HD. Disk Management in Windows shows the following:

[IMG]http://i.imgur.com/9DsWr.png[/IMG]

Does Windows 8 use a new GPT partition layout that Ubuntu does not understand?


Computer Specifications:
CPU: Pentium D 820
GPU: AMD x1400
RAM: 3GB DDR2
MB: Asus P5LD2
HD: 160GB AHCI

---

### Post by psrdotcom on 2012-06-01
Hi,

That is a strange think for me. Let me try that.

---

### Post by oldfred on 2012-06-01
I have had gparted not even see my sda drive when my old XP needed chkdsk even though XP would boot. I might try running chkdsk from Windows repair console.

Does this show partitions from liveCD/USB?

```
sudo fdisk -l
```

---

### Post by waspinator on 2012-06-01
well I found a work around, but it's not pretty.

1. I booted with an Ubuntu 12.04 USB stick.
2. Using gparted Ichanged the partition layout from GPT to MBR
3. Created a new primary partition for Window, and a logical partition for ubuntu
4. installed ubuntu to the logical partiiton with grub inside the root partition
5. installed windows 8 to the prepared partiton
6. installed [easybcd ]("http://neosmart.net/download.php?id=1")
7. used easybcd to add ubuntu to the windows boot loader. 

I actually prefer using easybcd and the windows bootloader now. It's so much easier to change boot options, and it looks less cluttered when booting.


I'm still amazed how well windows 8 runs. It's smoother than ubuntu, and I thought linux was supposed to be light weight. ubuntu seems so slow now. I might have to install windows 8 to bring some older ubuntu computers back to life.

---

### Post by TheKingOfComputers on 2012-06-01
If you're dual booting, use Wubi. Live-USB I'm almost positive is for COMPLETELY installing Ubuntu and getting rid of Windows. Plus, Wubi is a lot easier. Though, I don't recommend dual booting and the reason being it is very slow because your using almost all your memory. It is all being reserved. Thats what happened to me so I deleted Windows. Ubuntu now works like a charm. Choose one or the other bro.

---

### Post by critin on 2012-06-01
>  I might have to install windows 8 to bring some older ubuntu computers back to life.

Be sure those old computers can use at least 1g of memory.

---

### Post by critin on 2012-06-01
error post

---

### Post by Elfy on 2012-06-03
> **TheKingOfComputers said:**
> If you're dual booting, use Wubi. Live-USB I'm almost positive is for COMPLETELY installing Ubuntu and getting rid of Windows. Plus, Wubi is a lot easier. Though, I don't recommend dual booting and the reason being it is very slow because your using almost all your memory. It is all being reserved. Thats what happened to me so I deleted Windows. Ubuntu now works like a charm. Choose one or the other bro.

Live USB/Cd installation is NOT for completely installing Ubuntu and getting rid of windows. Please check what you are saying before you post.

Dual booting - please explain why it will be slower. When you are dual-booting you either boot on or the other. Linux and windows use memory in different ways - check it out.

> Choose one or the other bro.Is not any help for someone trying to dualboot.

---

