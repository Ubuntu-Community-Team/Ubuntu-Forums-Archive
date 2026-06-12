---
title: "Unable to boot in EFI?"
date: 2015-06-13
forum: Installation &amp; Upgrades
---

### Post by Jamie_Edwards on 2015-06-13
Hi guys,

So after hours and hours of trying to get this to work, and going on different forums... I've decided to give you guys a pop.

I recently decided to install Windows 8.1 in EFI and that kinda worked... I then decided to install Ubuntu 15.04 in EFI too (solely I might add) and It's also kinda worked.

Kinda? Well, Ubuntu wont boot in "secure mode". Here's what I mean, when I try to boot into Ubuntu, I get the "PC Repair" message from UEFI, stating it cannot find vital pieces to boot.

Strange I thought, and I must warn you now, this is the first time I've ever used UEFI!

But here's the thing, if I go into the BIOS and select Ubuntu in there, it boots normally... All be it in "Insecure Mode".

My question here is, how can I get UEFI to boot Ubuntu automatically? WITHOUT having to go into the BIOS each and every time?

Rig specs below:

Mobo: MSI 990XA-GD55
BIOS Version: E7640AMS V22.5
CPU: AMD Phenom II X4 B60
HDD: WD Caviar 120GB

---

### Post by oldfred on 2015-06-13
Did you install by booting with secure boot on, so it boots with shim(not grub) and kernels that are signed? Or perhaps even in CSM/BIOS mode, so you have to reboot to switch?

How you boot installer is then how it installs. There are really 3 versions. CSM/BIOS which is not-secure, UEFI which is not secure and the UEFI with secure boot.
But I consider secure boot oversold at the current time. In future we may need it, but the major BIOS based root virus was from Sony for its DRM music control.

I also do not believe you can boot Windows from grub menu with secure boot on. You can only use UEFI boot tab or perhaps one time boot key. With secure boot on, only systems installed with secure boot will be shown.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

        Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)

    
 MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)

---

### Post by Jamie_Edwards on 2015-06-14
> **oldfred said:**
> Did you install by booting with secure boot on, so it boots with shim(not grub) and kernels that are signed? Or perhaps even in CSM/BIOS mode, so you have to reboot to switch?

How you boot installer is then how it installs. There are really 3 versions. CSM/BIOS which is not-secure, UEFI which is not secure and the UEFI with secure boot.
But I consider secure boot oversold at the current time. In future we may need it, but the major BIOS based root virus was from Sony for its DRM music control.

I also do not believe you can boot Windows from grub menu with secure boot on. You can only use UEFI boot tab or perhaps one time boot key. With secure boot on, only systems installed with secure boot will be shown.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

        Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)

    
 MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)

With the whole Secure boot thing, I cannot find anywhere in my BIOS that can either enable or disable it.

EDIT:

I might be saying this a lot sooner than I should but I think I've fixed the problem... If I am right, I shall place what I did in another edit. (Likewise if it didn't actually work.)


EDIT 2:

So after restarting the computer, it seems to be booting normally without a hitch (although there's a different problem which I don't think is related to this thread)!

Here's what I did, I followed the "Systems that only boot Windows from UEFI" part of the following article.
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by sudodus on 2015-06-14
Yes, please :-)

Or even better, put it in another post (reply). It will help other users at the Ubuntu Forums to learn about your solution.

And finally, when you are sure, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by oldfred on 2015-06-14
My Asus motherboard does not call it secure boot.
It has a setting for Windows and 'other'. And only when I set 'other' does it open up the entries for CSM. And even though CSM is a totally separate chip from UEFI, under the CSM entry is all my UEFI settings. So I think secure boot setting is really the Windows/other setting.

---

### Post by Jamie_Edwards on 2015-06-14
I've scoured my MSI BIOS for the most minute mention of Secure Boot, or otherwise and there's nothing! It's like my mobo supports UEFI, but not actually support it, if you get what I mean.

---

### Post by oldfred on 2015-06-14
This says Boot mode select.

Bit hard to follow.
[https://www.youtube.com/watch?v=FuPDcbPWIG4](https://www.youtube.com/watch?v=FuPDcbPWIG4)

---

