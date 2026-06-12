---
title: "Problems with Ubuntu and Internal + external graphics cards."
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by nordemoniac on 2010-01-22
Hi!

This is a bug with Ubuntu OS, and then ofcourse all distros based on Ubuntu OS.

This is the problem:

I have a Intel D945GCLF2(D). It's a Atom 330 board with Intel GMA. In addition it has a PCI-slot, so you can install an external graphics card, f.ex. if you're in my situation and want a DVI port.

This won't work, for a lot of systems. This motherboard NEVER disables the internal graphics card. You can only set PRIMARY card.

This is a problem. I've been trying to install Ubuntu, using internal card, downloading the nVidia driver (which it suggests automatically), then in modprobe.d/blacklist.conf

```

blacklist agpgart
blacklist intel_agp

```afterwards, I would restart, go into BIOS, set external graphics as primary, and then put the monitor cable in the external card, and try to boot Ubuntu.

It won't start. Only gets to "TTY1", gnome doesn't start.

If I install using the external card, it stops during install of Ubuntu.


I've tried for so long, and I know this is a problem with how Ubuntu is detecting the card. Please find a method to make Ubuntu see that IF there is two graphics card detected, use the external (PCI), and software-disable internal card.

---

### Post by prshah on 2010-01-22
> **nordemoniac said:**
> 
I have a Intel D945GCLF2(D). it has a PCI-slot, so you can install an external graphics card, 

You can only set PRIMARY card.


I'm using D945GCL (not Atom) and Ubuntu works just fine with my PCI Express Nvidia card.

In the BIOS, I have options to set the primary card as PCI, PCI-E or Integrated. Have you chosen the correct option between PCI and PCI-E (if you have such an option?)

I don't need to blacklist any intel modules, either.

---

### Post by nordemoniac on 2010-01-23
> **prshah said:**
> I'm using D945GCL (not Atom) and Ubuntu works just fine with my PCI Express Nvidia card.

In the BIOS, I have options to set the primary card as PCI, PCI-E or Integrated. Have you chosen the correct option between PCI and PCI-E (if you have such an option?)

I don't need to blacklist any intel modules, either.

I have the options:

External (Which is PCI)
Integrated
Auto

Can't get it working, dunno why. Seems to me that Ubuntu just can't manage to choose which graphics card to use.

Is there any boot flags that can correct? Anything at all?

---

### Post by nordemoniac on 2010-01-25
I found this guide: [http://www.albertomilone.com/nvidia_intel_integrated.txt](http://www.albertomilone.com/nvidia_intel_integrated.txt)

But xorg.conf is no longer available in 9.10.

Where can I adjust these settings?


I've tried everything else in the guide, but the xorg.conf was skipped, and it didn't work.


Any way of enabling the xorg.conf file, or is there a other conf file to modify?

---

### Post by nordemoniac on 2010-01-25
I came a little further:

1. Connected two monitors, one to integrated VGA, and one to DVI on PCI-card.

2. Configured BIOS to have integrated VGA as primary.

3. Installed Ubuntu 8.04 (Has xorg.conf, and little problems with PCI-cards)

4. Booted Ubuntu 8.04 (still using integrated VGA) and started terminal

5. Used the command "**lspci -x**" and found my nvidia-card. "4:0:0"

6. Used the command "[B]sudo apt-get install nvidia-glx"

[/B]7. Then the command "**sudo nvidia-glx-config enable**" (will not always work)

8. Added nvidia to /etc/modules so it will load at startup. Just write "**sudo nano /etc/modules"** and add "**nvidia**" at the end.

9. Write "**sudo nano /etc/modprobe.d/blacklist**" and add "**blacklist agpgart**" and "**blacklist intel_agp**" at the end.

10. Edit xorg.conf with "**sudo nano /etc/X11/xorg.conf**". I found a "device" that said "VGA Adapter" or something like that, and edited it. Min looked like this after editing:


```
Section "Device" 
  Identifier "nVIDIA Corporation NV44A [GeForce 6200]" 
  Driver "nvidia" 
  BusID "PCI:4:0:0" 
    Option "NvAGP" "1" 
    Option "RenderAccel" "true" 
EndSection
```
11. Reboot and enter the BIOS Settings. Set external as primary (PCI)

12. Look at the screen connected to the PCI-card (or just switch the cable if you have one monitor.)


It worked!


I'm now going to export the xorg.conf to my Ubuntu 9.10, or XBMC 9.11, and try to make this work. I will have to blacklist under that OS to, and enable under modules, and hopefully this + a xorg.conf file will fix my problems.

---

### Post by nordemoniac on 2010-01-25
I tried installing XBMC Live 9.11-repack using the integrated VGA.

It installed, and shutdown, then when I rebooted (still using the integrated VGA), it wouldn't start. It got errors before even managing to start GDM. 

BUT!!

I changed the xorg.conf file (XBMC Live 9.11 had one) and changed it to the information listet in the post above.

As I closed and saved xorg.conf, the main monitor (connected to PCI) suddenly starts, and shows "XBMC" logo. So the desktop manager started on the second screen.

I have blacklisted intel_agp and agpgart, in addition to add "nvidia" at the end of "/etc/modules", but I'm unsure if this is necessary.



There's one problem though, but it might be OK - at least for now;

I CAN'T set PCI as primary card. Then I just get the old errors again. What I will need to do is set the integrated card as primary, then the computer shows BIOS, post, and boot on the primary VGA, but it then switches to the external card.

This really isn't a problem, only when in need to change something, or if exiting the desktop manager, because then everything is displayed on the other screen.

I'm going to use this as a HTPC with XBMC Live (Ubuntu 9.10) so actually, not seeing anything at the boot, before XBMC suddenly shows up, makes it look more like a set-top box, so I guess it's fine.

Aah... It's so good to finally get things to work.

---

### Post by nordemoniac on 2010-01-25
Tried removing the blacklisting of "intel_agp" and "agpgart" from "/etc/modprobe.d/blacklist.conf" and remove "nvidia" from the end of the "/etc/modules" file.

So now the system is actually default, but with a changed xorg.conf file. I guess in Ubuntu 9.10 (which doesn't have xorg.conf), importing the xorg.conf I made in Ubuntu 8.04 might correct the problems.

Well, this actually fixes my problems, but I would like everything to be seen on my DVI-screen. But as I said, it causes a better set-top box feeling, so maybe it's just for the good.

---

