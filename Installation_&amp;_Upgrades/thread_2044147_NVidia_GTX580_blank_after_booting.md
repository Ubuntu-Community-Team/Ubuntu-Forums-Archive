---
title: "NVidia GTX580 blank after booting"
date: 2012-08-18
forum: Installation &amp; Upgrades
---

### Post by sinukas on 2012-08-18
Hello,

I am using an nvidia gtx580 in my desktop and it's made it very difficult to install ubuntu 12.04. After running the installer with 'noapic nolapic nomodeset' in the kernel options I was able to successfully install the OS, however, when the installer reboots the system I cannot reboot into the OS. After passing BIOS, the screen goes blank (black) with the exception of a single blinking cursor in the upper left hand corner. I cannot seem to access GRUB or any other boot options to re-enable 'noapic nolapic nomodeset'. Is there a way to configure these options in the installer? What is the best way to work around this?

Thanks in advance

---

### Post by efflandt on 2012-08-19
What cpu do you have that you have to use **noapic** and **nolapic**?  For my GTX 550 Ti I had to use **nomodeset** when booting live/install iso (or I got just blinking cursor).  But once installed, nvidia-current was automatically installed during installation and I did not need any parameters for the installed system.

Are you sure that you installed grub to your hard drive (or wherever you installed Ubuntu to)?  12.04 is a little peculiar in that if you install from iso on USB, it might default to putting grub on the USB device you booted from.  So maybe you think you are booting the installed system, but are actually still booting USB.

If you do want to try using boot parameters for an installed system, press "e" during grub menu to edit the **linux** line.  Then if you find something that you need to use, you can add it to /etc/default/grub and run **sudo update-grub**

---

