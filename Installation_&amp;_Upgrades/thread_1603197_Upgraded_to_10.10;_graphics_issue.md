---
title: "Upgraded to 10.10; graphics issue"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by plzdontkillme11 on 2010-10-22
Hi,

Just last night I upgraded to 10.10. Everything went smoothly, except for one thing. When I boot, the background is white, and whenever I try to tweak the preferences, a few things happen.
1) The background flickers from white to my actual wallpaper
2) On my AWN Dock, a bunch of window images pop um titled "Unititled Window." These don't stay for long - they disappear as soon as the next window pops up so it doesn't hog the whole dock.

I hope I've given a good description of the problem. Of course, please ask for any technical information.

Thanks!

---

### Post by plzdontkillme11 on 2010-10-22
I can't believe I forgot to post this, but I'm using a Toshiba Satellite L305 with intel integrated graphics.

Here's some additional info.
```

vignesh@vignesh-laptop:~$ sudo lshw -C display
[sudo] password for vignesh: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3500000-d35fffff

```
```

vignesh@vignesh-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

---

### Post by Imxset21 on 2010-10-22
Are you using Compiz Window Manager? Sometimes you have to tweak those settings, too.

Also, do you have OpenGL installed?

---

### Post by plzdontkillme11 on 2010-10-22
Yes, I use CompizConfig. I'm not sure if I have OpenGL installed, is there a way to check?

---

### Post by plzdontkillme11 on 2010-10-22
I looked in Synaptic and saw a "Qt 4 OpenGL module" installed. Is this it?

---

### Post by plzdontkillme11 on 2010-10-22
Yeah, OpenGL is installed. Looked more thoroughly in synaptic.

---

### Post by plzdontkillme11 on 2010-10-22
UPDATE:

Graphics effects still work. For example, I enabled wobbly windows in compiz, and it runs without lag.

---

### Post by plzdontkillme11 on 2010-10-22
Ok, so the person in this link - [http://ubuntuforums.org/showthread.php?t=144131](http://ubuntuforums.org/showthread.php?t=144131) - has the exact same problem that I do. I tried the solution given, but there is no "current session" tab in gnome-session-properties. 

By the way, my background is now black with NO icons. I tried reinstalling xorg, which didn't work, and, just for the heck of it, tried to change my background. That's why it's like this now.

---

### Post by plzdontkillme11 on 2010-10-23
Bump.

---

### Post by plzdontkillme11 on 2010-10-23
Ok, two things:

1) I reinstalled Ubuntu using the instructions from this video:
[http://www.youtube.com/watch?v=QGnsYuWS0xY](http://www.youtube.com/watch?v=QGnsYuWS0xY)
Worked perfectly - but deskop is still pitch black and unresponsive. On a good note, I managed to fix all my sound issues.
2) I searched everywhere for a solution. I'm coming up empty handed. The one solution that I found doesn't work since I have a later version.

I have no idea what to do. To reiterate - everything works perfectly. The only issue: my desktop is gone.

---

### Post by plzdontkillme11 on 2010-10-23
Haha, FIXED! That was a nightmare.

---

### Post by omega0 on 2010-10-23
hello,

how did you fix your issue?  I am having a similar problem.  After upgrading from 10.04 to 10.10 the background is gray and a fuzzy image of everything I do is left in the background.  If I go to System > Administration> NVIDIA X Server Settings and change the resolution from auto to 1920x1200 and apply it resolves the situation, I get the background back and there is no fuzzy images in the background, until I restart the computer, then I need to do it again.

---

