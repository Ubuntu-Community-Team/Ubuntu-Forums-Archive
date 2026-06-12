---
title: "Kubuntu 11.10 next to Ubuntu 11.10 fails"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by Topsiho on 2011-10-24
Hello,

For experimental reasons I want a "clean" Ubuntu next to a "clean" Kubuntu. I have installed Linux distro's many times without problem next to Windows (dual boot). But this time it fails miserably.

(Already installed from year 0: Windows XP)
Installed first: Kubuntu 11.10.
Next installed Ubuntu 11.10

When after this I restart the computer, instead of a menuchoice for Kubuntu I get one for "MS-DOS 5.x/6.x/Windows3.1"!!! Grub2 of Ubuntu doesn't recognize Kubuntu!!!

I have changed /boot/grub.cfg in Ubuntu so that MS-DOS is replaced with Kubuntu, analoguous to the entry for Ubuntu, and was then able to log into Kubuntu. For a short while, because after updating Kubuntu I guess a new kernel was installed, and I'll have to change the grub.cfg again for the new kernel.

Doing (in Ubuntu) a sudo update-grub changes the Kubuntu entry to MS-DOS etc. again.

I know of course I just can install the Kubuntu-desktop into Ubuntu, but that's not what I want:

I want to know why Kubuntu is not recognized by the Ubuntu grub2, and how to circumvent this? Thank you.

:)


Topsiho

---

### Post by Topsiho on 2011-10-24
Bump

---

### Post by Topsiho on 2011-10-25
Bump. 

Is there really nobody out there who can explain that Ubuntu and Kubuntu can not be installed next to each other in a dual boot fashion, because the one recognizes the other as MS-DOS? (Ubuntu does).I know of course that I can install kubuntu-desktop in Ubuntu, but WHY can Ubuntu and Kubuntu not be installed next to each other?
Grub/Grub2 problems do not exist here, as both use grub2 (I think).

The existing Windows XP is recognized correctly, Ubuntu "recognizes" itself correctly, but the existing Kubuntu is not.

Only thing that I can think of is that this "feature" is implemented on purpose, to avoid double update downloads.

Topsiho

---

### Post by raja.genupula on 2011-10-25
> **Topsiho said:**
> Bump. 

Is there really nobody out there who can explain that Ubuntu and Kubuntu can not be installed next to each other in a dual boot fashion, because the one recognizes the other as MS-DOS? (Ubuntu does).I know of course that I can install kubuntu-desktop in Ubuntu, but WHY can Ubuntu and Kubuntu not be installed next to each other?
Grub/Grub2 problems do not exist here, as both use grub2 (I think).

The existing Windows XP is recognized correctly, Ubuntu "recognizes" itself correctly, but the existing Kubuntu is not.

Only thing that I can think of is that this "feature" is implemented on purpose, to avoid double update downloads.

Topsiho

Hi man 

   install Grub customizer in Ubuntu and then give a entry of Kubuntu in it.
[http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html](http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html)

---

### Post by Topsiho on 2011-10-25
Ha thanks,

I'll try this.

I'll tell whether this advise was succesful or not.
Starting up my experimens computer now :)

Topsiho

---

### Post by Topsiho on 2011-10-25
I followed the link of Ubuntugeeks, but so far have no succes with the grub-customizer: Kubuntu is changed to MS-DOS etc every time I change this. The OS prober is defective I think.

As I have to quit now, I´ll experiment later. I also have to find out whether the kernel image for Kubuntu 11:10 was updated, and to what kernel, in order to do the copying act again, from the Ubuntu entry.

Bye for now :)

Topsiho

---

### Post by Topsiho on 2011-10-25
Hello raja.genupula,

I'm afraid that your suggestion doesn't work. Every time, the entry is reverted again to the MS-DOS one.

Thanks for giving me this advice, though. Made me learn something, and that is what experimenting is for :)

I allready knew, but quite forgot, that changing grub.cfg as I did before, now, after an update, doesn't work anymore. No new kernel though, as I could find out from inspecting from Ubuntu.

Greetz from
Topsiho

---

### Post by Topsiho on 2011-10-26
I reinstalled Kubuntu, next to Windows and Ubuntu:

sda1 Windows
sda5 Ubuntu
sda9 Kubuntu

with /home and swap in sda6 and sda7 for both Ubuntu and Kubuntu.

Result is I now get a grub menu:

Ubuntu, with Linux 3.0.-12-generic
Ubuntu, with Linux 3.0.-12-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest 86+ console 115200)
Ubuntu, with Linux 3.0.-12-generic (on /dev/sda5)
Ubuntu, with Linux 3.0.-12-generic (recovery mode) (on /dev/sda5)  
Kubuntu, with Linux 3.0.-12-generic (on /dev/sda5)

The first and second entries should read Kubuntu.
The last entry doesn't work, gives me Busybox.

But now I can start Kubuntu, Ubuntu and, or rather, or Windows.

My conclusion is that Grub2 in (K)Ubuntu is a mess, sorry to say that.

For myself, I consider this thread as closed.

Topsiho

---

