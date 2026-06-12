---
title: "Lubuntu/Debian__Grub V2"
date: 2014-12-27
forum: Installation &amp; Upgrades
---

### Post by Freiklite on 2014-12-27
Hi,
Dual-boot > Debian/Lubuntu

My problem: run Debian from Grub V2. (GNU GRUB version 2.02~beta2-15)
BootInfo:
[http://paste.ubuntu.com/9631090/](http://paste.ubuntu.com/9631090/)

My Hardware: Notebook Toshiba satellite C70D-B- 11F, AMD-A8 and AMD-RADEON.

My problem description:
My installation from Toshiba/Windiows 8.1.
    I install Debian wheezy 7.7.0 (entire disk).

    I note that netinst forgets the question : 
    Install Grub &#65279;to the Master Boot Record (MBR)? » (man-db configuration).

    At the end I reboot and several messages appear:
        No bootable device --Please restart system
        >>start PXE over IPV4; press [ESC] to exit
        PXE-E18 : server reponse Timeout
        >>start PXE over IPV6; press  [ESC] to exit
        No bootable device -- Please restart system
    In other respects:
        boot failure: a proper digital signature was not found. One of the files on the select boot device was rejeted by the secure boot feature.

I am not able to run Debian from the terminal.

I install Lubuntu 14.10 (dual-boot); nothing to report.

The Grub display is:
    1 >> Lubuntu 14.10
    2 >> Lubuntu advanced options
    3 >> Debian GNU/Linux (7.7) (on /dev/sda2)
    4 >> Debian advanced options
    5 Setup

If I run 1 all is correct.
If I run 3     Init Version 2.88 booting
        etc,
        Starting common unix printing: cupsd
then black screen with blinking cursor.

At that moment I must switch off the computer.
End.

Thank you for your suggestions,
Bye.

---

### Post by oldfred on 2014-12-27
You have both installs in UEFI boot mode which is good that they are same. And then you do not have grub installed to the MBR, as that is only for BIOS/CSM boot mode.

But Boot-Repair says you have secure boot on, but Debian is not showing signed kernels? 
That would possibly explain this error:
boot failure: a proper digital signature was not found.
Does it have signed kernels like Ubuntu? Do not know details of Debian and if it supports secure boot or if all kernels are really signed or not?

Have you tried booting with secure boot off?

---

### Post by Freiklite on 2014-12-29
Hi,
" booting in insecure mode" produces the  same effect,  screen black with winking cursor.


In [https://www.debian.org/releases/wheezy/amd64/release-notes/ch-installing.en.html](https://www.debian.org/releases/wheezy/amd64/release-notes/ch-installing.en.html)
I found :
UEFI boot
       It is now possible to install PCs in UEFI mode instead of using the       legacy BIOS emulation.     

       Note that this does not include support for UEFI Secure Boot.     

??

---

### Post by oldfred on 2014-12-29
So you must have secure boot off.

Then black screen is usually video issue. Again not sure with Debian but AMD may need video settings.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
Not familiar with AMD and what video may be best.
       AMD drivers alternatives
[http://ubuntuforums.org/showthread.php?t=2256824](http://ubuntuforums.org/showthread.php?t=2256824)

   open (Gallium3D) and closed-source (Catalyst) driver

            [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)

---

### Post by Freiklite on 2014-12-31
Hi,
I tried nomodeset, acpi and differents options without success, with  secure boot or  with insecure boot.
I am seeking after the solution.

Ciao and happy new year.
):P

---

### Post by Freiklite on 2015-01-02
Hi,
I found this sentence in /var/log/Xorg.0.log:
[    71.841] (EE) Screen(s) found, but none have a usable configuration.

then
[materiel-installation-sur-asus-k551ln-blocage-touchpad-t50257.html]("http://www.debian-fr.org/materiel-installation-sur-asus-k551ln-blocage-touchpad-t50257.html")
In debian repairs mode:
**Code:**
in root


Xorg -configure 
(création of /root/xorg.conf.new)

then
cp /root/xorg.conf.new /etc/X11/xorg.conf
then

exit  
log in window appears.

Thank you very much.
Bye.

---

