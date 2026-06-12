---
title: "Eee PC:  After installation system boots to console"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by fantab on 2012-11-10
I bought ASUS Eee PC 1015CX (10" Netbook). It has following SPECS:

Processor: Intel ATOM N2600 - NM10 Express Chipset - 1.6Ghz - 32bit (EMT64=Not Supported)
Memory: 2 GB DDR3 (onboard)
Graphics: Intel GMA 3600 - Resolution: 1024x600

Info from BIOS menu:
ASUS Eee PC ACPI BIOS 
(I guess this is not UEFI, not sure though.

Now, I have installed Xubuntu 12.10 32bit. The Live USB .... It displays 'Try Xubuntu' and 'Intall Xubuntu' screen.... but nothing happens when I want to 'try xubuntu'.

**After Reboot my Netbook boots in text mode only... I get a console prompt to login.** :(
I don't see Grub Menu. If I use shift during boot I sometimes get Grub Menu and sometimes I don't. 

I need forum help to get my said Netbook going. Any help and any pointers will help. 

Thanks,
Regards.....

---

### Post by coldraven on 2012-11-10
I'm not sure if the following will apply to your problem.
I installed Ubuntu 12.04 on an Asus eeepc 900.
In the BIOS was an option for "Boot Boost" or something similar, I read that this should be disabled before installing.
On the HDD is a small partition (~2MB) called "BIOS" and AFAIK this can be read by the hardware BIOS to speed up the boot process. So I left it there and after a painless and successful install I hid it by editing the fstab.
(I created a folder called /mnt/asusbios and mounted it there)
I don't know if that was necessary but it works fine and is nice and fast.

---

### Post by fantab on 2012-11-10
I don't have that option in my BIOS. 
I have formatted my Hard disk, so nothing ASUS exists on the HDD :(

---

### Post by ugm6hr on 2012-11-10
Seems the problem is GMA 3600 graphics card:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031)

According to 1, you may have better luck with 12.04:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031/comments/14](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1069031/comments/14)

---

### Post by fantab on 2012-11-11
Thanks ugm6hr.

Having problems with most of my familiar distros I tried Bodhi Linux 32bit... This one boots if I tweak the kernel line by **adding 'nomodeset' and removing '$v7_handoff'** .  I can add nomodeset to /etc/default/grub and make it permenant but I haven't figured out yet, how to remove this '$vt_handoff' permanently from the kernel line. Any help regarding this how to will be appreciated.

I found Cedar drivers in the repos and installed them... Now, the system hangs after splash screen with following Error:
```
brcms-ops-config : Error setting power_level
```And after this nothing. The system puts out same error line one after another....

**Any ideas what is going on and how to resolve this?**

---

### Post by carl4926 on 2012-11-11
Just wondering if it was OK in the live session before install?

Have you tried the android for eeepc?

---

### Post by fantab on 2012-11-11
> **carl4926 said:**
> Just wondering if it was OK in the live session before install?

Have you tried the android for eeepc?

Yes, Bodhi LiveUSB works out of the box. And No I haven't tried Android.

---

### Post by carl4926 on 2012-11-11
> Yes, Bodhi LiveUSB works out of the boxBut is that only with nomodeset? Which would result is a poor graphics.

Android can be found here
[http://android-x86.googlecode.com/files/android-x86-2.2-r2-eeepc.iso](http://android-x86.googlecode.com/files/android-x86-2.2-r2-eeepc.iso)

---

### Post by fantab on 2012-11-11
No, the live usb works WITHOUT nomodeset...  Its only after installation that I have to use 'nomodeset'... Since CedarView and GMA 3600 drivers are available I suspect that the solution is around ... 

I will try Android if none of my preferred flavors work...

---

### Post by ugm6hr on 2012-11-12
I'm confused as to what you have tried.

Based on the bug report, 12.04 (which is the base for Bodhi) offers restricted driver for this. I presume this is what the LiveUSB defaults to.

Have you tried this post-install (or on an unadulterated *buntu 12.04)?

---

