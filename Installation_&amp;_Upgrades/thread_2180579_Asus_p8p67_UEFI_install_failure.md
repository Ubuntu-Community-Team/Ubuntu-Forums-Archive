---
title: "Asus p8p67 UEFI install failure"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by shdw.puppet on 2013-10-13
Hey guys,

I have tried, several times, to install ubuntu 13.04 on my desktop and each time I try to boot into the new install, I get a black screen with a single blinking white bar, similar to the terminal entry prompt.

System Specs
Asus P8P67 Motherboard
16gb RAM
i5 2500k
SanDisk 240 gb SSD (the harddrive I am trying to install on)

I go into the installer, let it do it's thing. Gparted says that the SSD looks like this after install
[http://imgur.com/b5jLbuY](http://imgur.com/b5jLbuY)

Since it failed, I go back into the live environment and install/run boot-repair, which kicks this out at the end
[http://paste.ubuntu.com/6233317/](http://paste.ubuntu.com/6233317/)

However boot-repair does not solve my problem, the same error comes up.

[http://i.imgur.com/OMl2DK9.jpg?1](http://i.imgur.com/OMl2DK9.jpg?1) - That is my UEFI screen

I have searched around, but anything I find either tells me to use boot-repair or is incomprehensible to me/not applicable to my problem.

Any help would be much appreciated.

---

### Post by oldfred on 2013-10-13
You show Ubuntu in efi partition. It should show in UEFI menu unless you have secure boot on as then only secure boot systems will show. Or you can use Boot-Repair to convert to the signed kernels and grub for secure boot, if you boot Boot-Repair in secure boot mode.

You may not get grub menu as you have only one system installed. Normally to see menu you have to hold shift key until menu appears, but some with UEFI systems find escape key works.

And if only Intel graphics you may need a different boot parameter than the standard nomodeset. I might try nomodeset first.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

   Some other boot options
acpi_osi=Linux  acpi_backlight=vendor

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

      
 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

---

### Post by shdw.puppet on 2013-10-13
Thank you for your help, the graphics settings did it for me.

---

### Post by oldfred on 2013-10-13
Glad that worked.
I posted several alternatives, which one(s) worked for you?

---

