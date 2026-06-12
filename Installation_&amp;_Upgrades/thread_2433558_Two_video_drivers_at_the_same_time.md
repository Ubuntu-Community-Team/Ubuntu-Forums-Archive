---
title: "Two video drivers at the same time?"
date: 2019-12-20
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2019-12-20
I ported Xubuntu 18.04 (up to date) from my old computer to my new Thinkpad P73. The display on the old computer was 1920x1080, but the new computer is 3840x2160, and has an NVIDIA  Quadro T2000 4GB. I anticipated video difficulties, in fact a black screen would not have surprised me. In fact, the display came up just as it should, 3840x2160. However, it took a long time to boot, and a lot of that time was spent trying and giving up on various NVIDIA drivers. Don't ask me why, but I had half a dozen NVIDIA drivers installed, plus the nouveau driver as well. At that time I used lshw -c video and discovered that the NVIDIA chip was 'unclaimed' and that the video was being handled by the Intel chip. To fix this I used Synaptic to uninstall all of the NVIDIA drivers, and then install just one - the 440 driver. 

Holding my breath I rebooted, and was greeted with a black screen. Maybe I uninstalled too many packages. I had previously downloaded the proprietary driver from NVIDIA (441), so I decided to install it. It took half an hour before I gave up trying to stop the X service, and decided to reboot to a root shell instead. When I rebooted I didn't hit Esc soon enough to get the Grub menu and it continued to boot. But this time it booted normally. Apparently it found the 440 driver that I had installed with Synaptic previously.

I was curious how it managed to boot, so I did lshw -c video again. And this is what I got:

  ```
*-display                 
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:185 memory:ea000000-eaffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:2000(size=128) memory:eb080000-eb0fffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:183 memory:e9000000-e9ffffff memory:c0000000-cfffffff ioport:3000(size=64) memory:c0000-dffff
```

Modinfo says that the NVIDIA hardware is using the 440 driver. 

I am thoroughly confused. How can both be running at the same time? If I was a video driver I would be sorely vexed. I thought video drivers and displays were supposed to be monogamous. How can two video chips be sending data to the same monitor at the same time? Can someone clue me in here?

---

### Post by CatKiller on 2019-12-20
> **John Jason Jordan said:**
> How can two video chips be sending data to the same monitor at the same time? Can someone clue me in here?

It's called Optimus. The idea is that you only use the Nvidia chip when you have to and the rest of the time you use the Intel chip to save the battery. It can be a complete pain in the bum. The gods of finicky software smiled on you today; hope that you stay in their favour.

---

### Post by John Jason Jordan on 2019-12-20
> **CatKiller said:**
> It's called Optimus. The idea is that you only use the Nvidia chip when you have to and the rest of the time you use the Intel chip to save the battery. It can be a complete pain in the bum. The gods of finicky software smiled on you today; hope that you stay in their favour.

Thanks. I owe you a beer!

---

