---
title: "How to make the Ubuntu 11.10 Live CD use a certain display driver?"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by drthrd on 2011-12-28
Version 11.10 is hanging on me. Parted Magic was doing the same thing. The problem with Parted Magic was the Nouveau driver, I had to use the nv driver. My video card is a Nvidia GeForce GTX 550 Ti. I think this is the same problem with Ubuntu 11.10. Is there a way to make the Ubuntu 11.10 Live CD to use a different driver?

---

### Post by drackololord on 2011-12-29
Hello [drthrd]("http://ubuntuforums.org/member.php?u=1315174"):

Perhaps you would like to look to this, if you are an advanced Debian user [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

it could help you, but far as id know Ubuntu loads its generic (included with the live cd) drivers, you  know for the bla bla stuff of Nvidia copyright drivers, but I do not understand, what is the relationship between parted magic and the Nouveau driver??, I do not get it, you mean you cannot see clear that program using Nouveau driver???

:o

Well, and it could help if you specify if it is 32 or 64 bits your distro and so on the Live Cd

sorry for my english, I am improving it (=

cheers pal

---

### Post by 2F4U on 2011-12-29
If I understand you correct, your card needs the proprietary nVidia driver instead of the open source one. The proprietary driver is not contained on the liveCD because it is not GPL. You would have to create your own liveCD, since Ubuntu's code of conduct forbids it to distribute non open source software.

---

### Post by drackololord on 2011-12-29
:PCool! Im glad that you understood my message [2F4U :)]("http://ubuntuforums.org/member.php?u=1357554")

Yes, I think so, we must be right, instead, that was what you were looking to do, do not you?

Run your own driver instead of generic, on a Live Cd Ubuntu, do not you?

In my opinion making your own Live cd looks a little exhausting but a good way to make it, instead of installing it every time you run your live cd!


:popcorn:


Well, if my answer helped you, you shoul mark this thread  as solved

:razz:=;

---

### Post by efflandt on 2011-12-29
The simple solution is to use **nomodeset** kernel boot parameter.  That seems to allow nouveau in 64-bit 11.10 iso to work with GTX 550Ti

```
01:00.0 VGA compatible controller: nVidia Corporation GF116 [GeForce GTX 550 Ti] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device 1556
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f8000000 (32-bit, non-prefetchable) [size=32M]
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at d4000000 (64-bit, prefetchable) [size=64M]
    I/O ports at dc00 [size=128]
    Expansion ROM at fbc80000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel modules: nouveau, nvidiafb
```When you see the purple screen with symbols at the bottom, hit the space bar, select your language, then F6 and mark **nomodset**.  Esc gets you out of that so you can select to Try Ubuntu.  The resolution may not be perfect (1280x1024 on my 1080p HDTV), but it should work.

Actually it still loads nouveau once you get nvidia-current drivers in an actual installation:

```
01:00.0 VGA compatible controller: nVidia Corporation GF116 [GeForce GTX 550 Ti] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device 1556
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f8000000 (32-bit, non-prefetchable) [size=32M]
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at d4000000 (64-bit, prefetchable) [size=64M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fbc80000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb
```I don't know if nomodeset is still needed at that point or if that was left over from when I had trouble with a failing GT 430, but in /etc/default/grub I have:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

I am using drivers from xswat repository:

**dpkg-query -l nvidia***
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
un  nvidia-173                  <none>                      (no description available)
un  nvidia-180-modaliases       <none>                      (no description available)
un  nvidia-185-modaliases       <none>                      (no description available)
un  nvidia-96                   <none>                      (no description available)
ii  nvidia-common               1:0.2.35                    Find obsolete NVIDIA drivers
ii  nvidia-current              290.10-0ubuntu1~oneiric~xup NVIDIA binary Xorg driver, kernel module and VDPAU library
un  nvidia-current-modaliases   <none>                      (no description available)
un  nvidia-libvdpau             <none>                      (no description available)
un  nvidia-libvdpau-ia32        <none>                      (no description available)
un  nvidia-libvdpau1            <none>                      (no description available)
un  nvidia-libvdpau1-ia32       <none>                      (no description available)
ii  nvidia-settings             290.10-0ubuntu1~oneiric~xup Tool of configuring the NVIDIA graphics driver
un  nvidia-va-driver            <none>                      (no description available)
un  nvidia-vdpau-driver         <none>                      (no description available)
un  nvidia-vdpau-driver-ia32    <none>                      (no description available)
```

---

### Post by drthrd on 2011-12-29
> **drackololord said:**
> Hello [drthrd]("http://ubuntuforums.org/member.php?u=1315174"):

Perhaps you would like to look to this, if you are an advanced Debian user [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

it could help you, but far as id know Ubuntu loads its generic (included with the live cd) drivers, you  know for the bla bla stuff of Nvidia copyright drivers, but I do not understand, what is the relationship between parted magic and the Nouveau driver??, I do not get it, you mean you cannot see clear that program using Nouveau driver???

:o

Well, and it could help if you specify if it is 32 or 64 bits your distro and so on the Live Cd

sorry for my english, I am improving it (=

cheers pal

The default driver Ubuntu uses is the same one that Parted Magic uses, the Nouveau driver. [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) look there. For Parted Magic I had to use the "KILL Nouveau" option to get Parted Magic to fully load. It would hang and act like Ubuntu 11.10. I am using the 32 bit version.

---

### Post by drthrd on 2011-12-29
> **efflandt said:**
> The simple solution is to use **nomodeset** kernel boot parameter.  That seems to allow nouveau in 64-bit 11.10 iso to work with GTX 550Ti
When you see the purple screen with symbols at the bottom, hit the space bar, select your language, then F6 and mark **nomodset**.  Esc gets you out of that so you can select to Try Ubuntu.  The resolution may not be perfect (1280x1024 on my 1080p HDTV), but it should work.


Thank you that worked.

---

