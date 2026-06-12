---
title: "[SOLVED] Ubuntu 8.04 and NVIDIA proprietary driver"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by hardmath on 2008-10-27
I installed Hardy Heron on a new box, one built around an NVIDIA GeForce 6100 chipset and AMD64 X2 processor.

Everything worked fine until I enabled the NVIDIA proprietary driver!

I think the first time after rebooting I got a black screen.  Then I used the recovery mode option to auto-configure the xserver settings.  What I'm seeing now is that after login (which proceeds normally), the screen flickers a bit and goes white.  A movable mouse cursor appears on the screen, but everything else is white.  Possibly there is some "desktop" content hidden there, but I haven't been able to discern it.  I was able to do a mouse drag to "select" a bluish rectangle, but otherwise there seems no graphical user interface.

I tried doing dpkg-reconfigure xserver-xorg from the recovery mode command line, but it did not change the white screen phenomenon.

I'm game to rollback the NVIDIA driver or edit the xorg.conf file, but I'm at a loss to know whether I need to do one or the other first.  I've read suggestions about running nvidia-settings or nvidia-xconfig on other threads, but neither package is installed yet, and I had no luck trying to install them with apt-get in recovery mode.

regards, hm

UPDATE:  I was able to apt-get the nvidia-settings and nvidia-config packages by using the ctrl-alt-F1 trick to kill my XWindows session after the white screen appeared, kicking me back into a console login session.  There seems to be a problem with the NVIDIA display being defined.  The motherboard has both a VGA and an HDMI connector, though only the VGA connector is in use.  Running nvidia-xconfig the first time reported a "validation error" with no control display line in my xorg.conf file, but the second time I ran it there was no complaint.  Rebooting put me into a "low resolution" dialog mode, from which I was able to fall back to the generic VESA display driver.

UPDATE 2: Solved. The computer store where I'd bought the new case & motherboard had given me the wrong packaging and documentation.  Nvidia drivers don't work with ATI Radeon based graphics chips!!

---

### Post by logos34 on 2008-10-27
You could always try the official nvidia driver on the website (vers. 177.blah.blah)--maybe use Envy to install it.  But vesa should actually work fine for you if you don't need 3D or whatver.

good luck

---

