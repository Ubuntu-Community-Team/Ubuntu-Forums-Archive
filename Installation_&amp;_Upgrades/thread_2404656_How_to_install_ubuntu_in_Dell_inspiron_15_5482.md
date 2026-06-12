---
title: "How to install ubuntu in Dell inspiron 15 5482"
date: 2018-10-26
forum: Installation &amp; Upgrades
---

### Post by arbiculario on 2018-10-26
Hi,

I'm trying to install ubuntu in  Dell inspiron 15 5482, but I can't by the moment.

I'm trying to install in dual boot with Windows 10 (I prefer this option), but if it's easier to install Ubuntu without Windows I can think about it.

I don't know the exactly settings on the BIOS to run the live USB. I try some changes, but they don't work.

Can you help me, please?


Thanks.

---

### Post by oldfred on 2018-10-26
Typically with Dell you have to update UEFI from Dell, and if SSD update firmware.
You also have to change drive settings in UEFI from RAID to AHCI, but install AHCI drivers into Windows first, if you want to dual boot.
Only use Windows to shrink the NTFS partition and reboot immediately so it can run chkdsk. Make sure in Windows fast start up is off.
If nVidia, you need nomodest with live installer and initial boot until you install nVidia proprietary driver from Ubuntu repository (not nVidia directly).

General UEFI install instructions in link in my signature. Be sure to boot install media in UEFI boot mode.

       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[URL="https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en"]https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en
[/URL]
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL][URL="https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en"]
[/URL]

---

### Post by arbiculario on 2018-10-27
Hi, oldfred, thank you for your answer.

I have not found an UEFI update on dell.com. I have found a BIOS update, but I check my BIOS versión and it's the last one (1.3.0)

In my BIOS I have not found the drive settings to change RAID to AHCI.


Nevertheless, I think that my computer doesn't admit Secure Boot Disabled, because when I try to run my USB live with Secure Boot Disabled it doesn't run and appears a notice related with BitLocker. I think that BitLocker is the problem that blocks the installations when I disable Secure Boot. Is that possible? Can I set something to can install Ubuntu?

Thanks

---

### Post by oldfred on 2018-10-27
I have seen one or two other threads discussing bitlocker, but do not know any details.
I think it makes it difficult to dual boot and or use Ubuntu on same drive. You may need to install to a separate drive.

Found this in my notes:
       AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
[https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html](https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html)

---

### Post by arbiculario on 2018-11-02
Hi, 

I can install Ubuntu using another usb, seems that there was something wrong in the first one.

I had some troubles with bitlocker. I disabled it, but I couldn&#8217;t install Ubuntu on dual mode, because when I switched RAID to AHCI windows shows some errors.

Finally I installed Ubuntu alone and it works.

Thanks!

---

