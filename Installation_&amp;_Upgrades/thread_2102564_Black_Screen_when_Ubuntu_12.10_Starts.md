---
title: "Black Screen when Ubuntu 12.10 Starts"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by btedm on 2013-01-07
I have a dual boot PC with Ubuntu 12.04 and recently installed Ubuntu 12.10.  During the installation the first few tries the screen went black, but after several tries I was able to install 12.10 using nomodeset.  I was able to start 12.10 once, did a software update.  Also because of the problems with the black screen I installed the recommended nvidia driver.  Now the grub screen is OK, but when Ubuntu 12.10 starts the screen goes black and shows a message "vga in 1024X768 hsync 68.5 kHz vsync 84.5 kHz Clock 115 MHz".

In the file /var/log/Xorg.0.log I see the message:
```
[    20.512] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    20.512] (**) NVIDIA(0):     device VHT PV1710 (CRT-0) (Using EDID frequencies has been
[    20.512] (**) NVIDIA(0):     enabled on all display devices.)
[    20.512] (WW) NVIDIA(GPU-0): The EDID for VHT PV1710 (CRT-0) contradicts itself: mode
[    20.512] (WW) NVIDIA(GPU-0):     "1024x768" is specified in the EDID; however, the EDID's
[    20.512] (WW) NVIDIA(GPU-0):     valid VertRefresh range (50.000-75.000 Hz) would exclude
[    20.512] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (85.0 Hz); ignoring VertRefresh
[    20.512] (WW) NVIDIA(GPU-0):     check for mode "1024x768".
[    20.515] (WW) NVIDIA(0): No valid modes for "CRT-0:1024x768_60.00"; removing.

```

I assume from reading the above that nvidia doesn't like the Vertical refresh range of 50-75 Hz and used 85 instead, but the monitor does not work at this update rate.  I tried setting a mode of "1024X768_60" (based on modes from 12.04) in file /etc/X11/xorg.conf, but nvidia did not like this either.  
Does anyone know of a good way to set the mode or another work around for this problem?

---

### Post by btedm on 2013-01-13
I have some success and now have the monitor working.  From the black screen I was able to get a text screen with crtl-alt-F2.  I then logged in and entered the command ```
sudo nvidia-xconfig --no-use-edid-freqs
```
which I found in [http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-96-xconfig.1.html]("http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-96-xconfig.1.html").  I then rebooted and after some time the screen appeared.  I still need to get a bit higher resolution, but that should be a lot easier now.

---

