---
title: "AMD vidoe card Chip Type ATI Radeon 9200"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by esky64 on 2013-05-13
Hi I just newly instaled ubuntu 12.10
I can't get to change my video size 
My video card is onboard if I remember 
getting thjis info from pressing crtl alt+F1
01:00.0VGA COMPATABLE CONTROLLER: AMD [AMD] NEE ATI RV280 [RADEON 9200SE] (REV 01)
Can I cut and paste this somehow so I don't make a typo 
I'm also boot in clasic mode not unity
please ask for more info if needed
Thanks
Chris

```
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 SE] (Secondary) (rev 01)

chris@chris-desktop:~$ sudo lshw -C display
[sudo] password for chris: 
  *-display:0             
       description: VGA compatible controller
       product: RV280 [Radeon 9200 SE]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:16 memory:d0000000-d7ffffff ioport:a000(size=256) memory:e5000000-e500ffff memory:e4000000-e401ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 SE] (Secondary)
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 mingnt=8
       resources: memory:d8000000-dfffffff memory:e5010000-e501ffff
chris@chris-desktop:~$
```

---

### Post by dino99 on 2013-05-13
if you have an xog.conf, then delete it and let the kernel doing its own job  (sudo rm /etc/X11/xorg.conf)

for that card/chip, you need to install xserver-xorg-video-ati & xserver-xorg-video-radeon
( of course dkms, build-essential & the kernel(s) headers need at least to be installed first

---

### Post by esky64 on 2013-05-13
Quote
 you need to install xserver-xorg-video-ati & xserver-xorg-video-radeon
end Quote
Can you please explain to me how I do this I'm still learning linux 
Thanks

---

### Post by esky64 on 2013-05-13
chris@chris-desktop:~$ sudo apt-get install xserver-xorg-video-ati
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-ati is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@chris-desktop:~$ sudo apt-get install xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-radeon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@chris-desktop:~$ sudo rm /etc/X11/xorg.conf

---

### Post by esky64 on 2013-05-13
Thanks you very much all working now thank you again

---

