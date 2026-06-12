---
title: "help with LCD display under  gutsy"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by arupdg on 2008-04-18
I installed Gutsy on my Toshiba U300 without any problem. My LCD is  13.3" 1280X800 resolution and the driver in Mobile Intel Chipset Family 965 However the top and bottom menubars did not cover the full width of the screen though the desktop image covered the full screen. All windows, even when maximised did not fill the full screen.

I tried System> Administration > Screen(?) and saw the Drivers selected were different so I changed them to Intel 965 and BAM!

Now my Gutsy hangs after this comment
*Running local boot scripts (/etc/rc.local)

If I hit the restart key I get
*Stopping GNOME display manager
..and the system shuts down

I tried GRUB recovery mode option and get a command line interface which I am not familiar with.
I tried the GRUB e option but got confused and retreated

How can I reset my display back to the original so I can get the installation back to work again?

Please help

---

### Post by Canuckelhead on 2008-04-18
> I installed Gutsy

Great!  What's the problem with the LCD?

---

### Post by arupdg on 2008-04-19
No problem with LCD. Gutsy hangs. My system is dual boot with Vista and Vista is working fine. The trouble started after I tried to change the display drivers to Intel 965 family. Gutsy had installed a default driver and the display was working but not using the full width of my screen.

---

### Post by confused57 on 2008-04-19
In Recovery mode, you can reconfigure your xorg:
```
dpkg-reconfigure xserver-xorg
```
You may want to try using the "vesa" video driver to at least get to a GUI, then you can try installing the driver for your video card chipset.

---

### Post by arupdg on 2008-04-19
OK will try that. Just a thought. If the system creates a backup then I can restore that file. Where will such a file reside?

O boy! Did as you suggested and accepted all defaults. My system is back! Thanks. :biggrin:

But I still have the monitor using only 1024X768 of available 1280X800 pixels. Any suggestions?](*,)

---

