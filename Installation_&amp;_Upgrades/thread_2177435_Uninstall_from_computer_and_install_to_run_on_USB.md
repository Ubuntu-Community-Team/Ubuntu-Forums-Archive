---
title: "Uninstall from computer and install to run on USB"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by ddubbz1979 on 2013-09-28
I am dual booting 13.04 with Windows 7 currently.  Getting frequent crashes.  Especially when I use Firefox.  Chrome is the only thing that works, and especially with videos, however, still get a crash from time to time.  Thought since I'm new to Linux I would buy a large capacity USB drive and try to boot from there on my multiple computers rather than install Ubuntu on all of them.  Looking for advice on how to uninstall from my system properly and get my partitioned drive back onto windows, As well as how to install on a USB to run.  Also looking for advantages and disadvantages of doing this if anyone would be so kind to share.  Thanks in advance.

---

### Post by whitesmith on 2013-09-28
Okay, I'll play Mr. Downer. One disadvantage is that USBs are nowhere near as fast as HDDs, especially SSDs. Others can, and probably will, comment on the installation issues your plan will raise. Good luck in your endeavor.

---

### Post by sudodus on 2013-09-28
> **ddubbz1979 said:**
> I am dual booting 13.04 with Windows 7 currently.  Getting frequent crashes.  Especially when I use Firefox.

Is Windows or Ubuntu or both crashing?
> 
Chrome is the only thing that works, and especially with videos, however, still get a crash from time to time.  Thought since I'm new to Linux I would buy a large capacity USB drive and try to boot from there on my multiple computers rather than install Ubuntu on all of them.  Looking for advice on how to uninstall from my system properly and get my partitioned drive back onto windows

Do you intend to move your system to the USB drive, or would you be happy to make a fresh install (and only move your personal files (documents, pictures, media files)?

Do you have some installation media for Windows? Install disk, recovery disk ...? If not, maybe you should keep the boot directory of Ubuntu (with the grub files). Is Windows 7 installed with UEFI or standard BIOS? 'Everything' is more difficult with UEFI.

When you have saved/moved what you need, you can let Windows take back the space used by Ubuntu.
> 
As well as how to install on a USB to run.  Also looking for advantages and disadvantages of doing this if anyone would be so kind to share.  Thanks in advance.

If you can use the whole USB drive, you can use the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") to install a suitable Ubuntu based version or flavour. Remember that USB 2 is rather slow, so it is worthwhile using a light-weight desktop environment even if the computer is powerful. USB 3 and eSATA provide fast connections. See this link for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

