---
title: "Boot stops at &quot;Loading initial ramdisk&quot;."
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by verm2 on 2013-12-07
I have a laptop MSI GE40.

I try to install Ubuntu but GRUB won't launch it.

Boot stops at "Loading initial ramdisk".

The problem is similar to
[http://ubuntuforums.org/showthread.php?t=2184191](http://ubuntuforums.org/showthread.php?t=2184191)

---

### Post by Bucky Ball on 2013-12-07
***Post moved to own thread.***

Which release are you using?

---

### Post by verm2 on 2013-12-07
I'm using Ubuntu 13.10

---

### Post by Bucky Ball on 2013-12-07
How far do you get? Do you get to the list of options 'Try Ubuntu' 'Install Ubuntu' etc.? What do you choose if you do? Have you tried it from 'Try Ubuntu'? How long have you waited for it to hang at that screen? It can take awhile, depending on the machine and configuration. 

What are the specs of the machine?

Try and include as much info about what you've done.

---

### Post by verm2 on 2013-12-07
My laptop is MSI GE40 i7-4702MQ, Nvidia GTX 760M, 16 GB RAM, Windows 8.1

I have the same problem like [http://ubuntuforums.org/showthread.php?t=2184191](http://ubuntuforums.org/showthread.php?t=2184191)

> GRUB launches while in UEFI mode and boots into Windows fine, but if I attempt to run Ubuntu I am greeted by a frozen purple screen. 

Running Ubuntu recovery has the same effect, except with a black screen. 

I've tried nomodeset as suggested in numerous previous posts, the Boot-Repair utility, and every other fix I could find on this forum and the web at large (including a non-graphical boot). None of these seem to make any difference. 

I first installed Ubuntu in Legacy BIOS mode, and when it was installed like that I could boot into Ubuntu with the Legacy BIOS selected, and windows with UEFI. I then used Boot Repair to make it boot in UEFI. 

Now that GRUB comes up in UEFI, I can only boot windows and windows recovery, but neither of the Ubuntu options.

Thanks in advance.

---

### Post by oldfred on 2013-12-07
Is this dual video and you really are booting with the Intel chip? Nomodeset works for nVidia, but if booting with Intel you may need Intel settings or force it to boot in one of the lower level drivers like it probably was doing with live installer or BIOS boot install.

       Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

Older:

  xforcevesa 
nouveau.modeset=0

      
 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

### Post by verm2 on 2013-12-07
Thank you for your help.

I'm trying to boot Ubuntu with this options:

linux /boot/vmlinuz-3.11.0-14-generic root=UUID=<...> ro quiet splash $vt_handoff xforcevesa nouveau.modeset=0 acpi_osi=Linux acpi_backlight=vendor i915.i915_enable_rc6=1 video=VGA-1:1280x1024-24@60
initrd /boot/initrd.img-3.11.0-14-generic

But boot stops as before

---

### Post by oldfred on 2013-12-07
I do not think you can add all of them as each is for different Intel chips or configurations. And the older versions will conflict as each is a different older video driver. 
Each line posted above is one boot option to try.

---

### Post by verm2 on 2013-12-07
I have tried:

linux /boot/vmlinuz-3.11.0-14-generic root=UUID=<...> ro quiet splash $vt_handoff xforcevesa 
linux /boot/vmlinuz-3.11.0-14-generic root=UUID=<...> ro quiet splash $vt_handoff nouveau.modeset=0 
linux /boot/vmlinuz-3.11.0-14-generic root=UUID=<...> ro quiet splash $vt_handoff acpi_osi=Linux acpi_backlight=vendor
linux /boot/vmlinuz-3.11.0-14-generic root=UUID=<...> ro quiet splash $vt_handoff i915.i915_enable_rc6=1
linux /boot/vmlinuz-3.11.0-14-generic root=UUID=<...> ro quiet splash $vt_handoff video=1280x1024-24@60
linux /boot/vmlinuz-3.11.0-14-generic root=UUID=<...> ro quiet splash $vt_handoff video=VGA-1:1280x1024-24@60

but boot stops

---

### Post by oldfred on 2013-12-07
I doubt if 1280x1024 is your size but if that type of parameter would have worked it would have booted but given weird video. You need to use your video x by y size.

I would have thought that vesa or nouveau modes would have booted just like live installer as I think that is the lowest level driver.

So it may need other boot parameter in addition?? That becomes difficult to know what to use unless someone with a similar system has posted somewhere.

Does boot stop or does it give error message. Usually removing the quiet splash lets you see boot process and then you may see where it stops. Actual line it stops on is often not the issue but a few lines up may be errors or warnings.

---

### Post by verm2 on 2013-12-08
The bug is described here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)

There is no solution yet

---

