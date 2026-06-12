---
title: "Purple/Black screen after installing 13.04 64bit"
date: 2013-09-16
forum: Installation &amp; Upgrades
---

### Post by Michael_Symons on 2013-09-16
Here is my system:
[http://www.mytoshiba.com.au/products/computers/qosmio/x70/psplta-014001/specifications](http://www.mytoshiba.com.au/products/computers/qosmio/x70/psplta-014001/specifications)

Note the NVidia 770m + optimus

I have recently with much difficulty managed to install 13.04 64bit.

After setting these paremeters, I have finally managed to see where the boot up process has crashed. I will include some of the output that I managed to write down below:
=================={Bootloader options}==========================
acpi_osi=Linux
acpi_backlight=vendor
video=1920x1080@60
no splash

================={ approximate output}==================================

[9.764822] nouveau [DRM] : 3 performance levels
[9.765592] nouveau [DRM] 0: Core 202MHz Shader 405Mhz......................
[9.766367] nouveau [DRM] 1: Core........................................................(too lazy to write all this down)
[9.767142] nouveau [DRM] 3: Core........................................................
[9.767919] nouveau [DRM] c: fanspeed 1%

[38.853613] MCE [Hardware error]: CPU 0: Machine check exception: 0 Bank 5: ae0000000040110a
[38.854914] MCE [Hardware error]: TSC 0 ADDR ff887200 MISC 38a0000086
-------------- MCE [Hardware error]: 
-------------- MCE [Hardware error]: CPU 1:  Machine check exception: 0
-------------- MCE [Hardware error]:
-------------- MCE [Hardware error]:
-------------- MCE [Hardware error]: CPU 2:  Machine check exception: 0
-------------- MCE [Hardware error]:
-------------- MCE [Hardware error]:
-------------- MCE [Hardware error]: CPU 3:  Machine check exception: 0
-------------- MCE [Hardware error]:
-------------- MCE [Hardware error]:
-------------- MCE [Hardware error]: Some CPUs didn't answer synchronisation
-------------- MCE [Hardware error]: Machine check invalid!
Kernel Panic! - Not synching: Fatal machine check on CPU
Shutting down CPUs with NMI
DRM_KMS_helper: Panic occurred.
rebooting in 30 seconds.._
(((Computer freezes)))

Given this information, is anybody able to help me make Ubuntu bootable/usable?

Thanks,
Michael

---

### Post by Michael_Symons on 2013-09-17
I am currently downloading 13.10 to see if there is difference. Maybe a newer kernel could help.

---

### Post by Michael_Symons on 2013-09-17
=======UPDATE=======

I can NOW boot into linux with > acpi=off

Now my main concern is, I now have no power management! Everything is running at full power, the GPU and CPU are quite warm for no reason.

How can I fix this? 
How do i find out which ACPI module is causing the issue?

---

### Post by Michael_Symons on 2013-09-17
=======Update======

I've tried more parameters in the boot options
Here is the data I have collected
acpi=off         (boots but makes laptop hot)
acpi=ht          (fails)
pci=noacpi     (boots)
acpi = noirq    (boots, but no backlight)
pnpacpi=off    (fails)
noapic           (fails)
nolapic          (fails)
acpi=noirq AND acpi_backlight=vendor  (Boots)
acpi_osi=Linux AND acpi_backlight=vendor (Fails)

So now is the question... which of the following options will offer the most features of ACPI?
acpi=noirq AND acpi_backlight=vendor (boots)
pci=noacpi  (boots)

What should I do from here?

---

### Post by smuggly on 2013-09-17
Have you checked acpi options in your bios? I would check and see if some strange options are enabled.

---

