---
title: "Help me understand installation on UEFI"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by gunksta on 2015-03-18
Howdy!

I have been installing linux onto computers and laptops since 1999 but this weekend something happened I have never experienced before. I bought a new laptop / tablet (Microsoft Surface Pro 3) and installed Kubuntu on it. I installed Vivid, but quite frankly I don't think my problem was with Vivid, which is why I am posting this here. I don't use Windows, unless I am at work. So, read on-line how to boot into UEFI, put Vivid onto a flash drive and booted my new fondle-slab. I booted into Kubuntu and played around. Most things worked OKish, but it was all what I expected, out of the box, based on what I had read online.

I installed Kubuntu, wiping Windows out. I left Kubuntu do a clean installation with an excrypted LVM setup.

I rebooted . . . to nothing. 

Secure Boot is disabled. I can boot to the USB key, but not to my harddrive.

I reinstall, and this time opt for an encrypted home directory, thinking maybe UEFI support for encrypted LVM is lagging.

Rebooted to . . . . . nothing.

I can't get past the UEFI screen telling me it can't find anything. I proceeded to panic. Eventually, I reinstall Windows. I follow instructions for installing Linux for dual booting onto this hardware. I restarted my computer - and it worked.

OK. Great. I'm writing this post to you, from the keyboard of my shiny new Surface Pro 3.

But, I'd like to reinstall it and wipe out Windows and use encrypted LVM. So, how do I do that? I'm stuck and I suspect it is because of UEFI. This is the first system I have ever owned that doesn't have a legacy mode button.

I humbly await your wisdom.

---

### Post by TheFu on 2015-03-18
Posting the boot-info URL from **boot-repair** would be a help.  This way any tiny mistakes with partitioning might be found.

And you probably already saw this, but [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I can assure you that UEFI booting and whole drive encryption work fine with Ubuntu 14.04. I won't run any non-LTS releases. Need my systems to be supported longer than 6-9 months.

..... removed ..... it was booting in legacy mode due t specific hardware.

---

### Post by pmi2 on 2015-03-18
Here's another link.  The author of this article suggests that one can inadvertently install Linux in non-EFI mode on a system where EFI is active.  

Not sure that is what happened to you, but it's one possibility.  In other words, having a distribution medium with Linux that works perfectly well in EFI boot mode does not help if the installer (human or software) mis-identified what is suppsed to be installed (chuckle).

[http://www.rodsbooks.com/linux-uefi/#isitefi](http://www.rodsbooks.com/linux-uefi/#isitefi)

---

### Post by oldfred on 2015-03-19
I have seen several threads with UEFI & LVM full drive installs. It has an efi partition, the /boot partition and the physical partition where the LVM is inside. But not on a Surface Pro.

Since a Surface Pro is a Microsoft product you should automatically expect more issues as Microsoft is not Linux friendly. 

Some other Surface Pro threads.
 Surface Pro Ubuntu install:
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)
[http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946)
[http://ubuntuforums.org/showthread.php?t=2209247](http://ubuntuforums.org/showthread.php?t=2209247)

---

### Post by gunksta on 2015-03-23
Truthfully, I bought the Surface for two reasons.

1. I was curious how much harder it would be because the hardware is made by MS.
2. This is some genuinely awesome hardware.  The possibilities here are staggering. This is, quite frankly, the device I want (once I get all the parts working). A tablet AND a laptop. The battery life isn't up-to-par for a tablet, although it is perfectly acceptable for a laptop, and laptop-like performance is more important to me than long battery life.

At this point, I have installed the Ubuntu shim and can boot the laptop in secure mode, which is nice. I will probably just leave it alone for a while. It works, I'm not desperate for the space, and I'm not 100% sure I can make it work the other way . . . . it is after-all, a Microsoft product.

---

