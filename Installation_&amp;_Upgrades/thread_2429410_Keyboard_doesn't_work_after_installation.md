---
title: "Keyboard doesn't work after installation"
date: 2019-10-17
forum: Installation &amp; Upgrades
---

### Post by businessdog on 2019-10-17
After years of trying Ubuntu releases (and many other distros) and due to the release of Ubuntu 19.10, I decided to again try to install Ubuntu. During initial tries the keyboard was not working, but after a while, without me changing anything, the keyboard enabled me to write the wi-fi password to proceed with the installation. The problem of the previous installation tries of Ubuntu and other distros have been, if I am correct, the NVIDIA drivers. Since this release is supposed to include the proprietary drivers, I thought this could be it.

After installation, while booting for the first time, I did not have any keyboard input at the log in screen, even though I had it in GRUB. An external keyboard worked here. After logging in, I decided to try to switch to the noveau drivers, instead of the most recent proprietary NVIDIA drivers. Despite not booting for 3 or 4 tries, I eventually was able to log in and have keyboard input at the log in screen. Even though the keyboard was working, the graphics were very choppy, this being especially when scrolling looking through solutions in Firefox. I then decided to go back to the official NVIDIA drivers and try to solve the problems there. Despite booting, the laptop's keyboard did not work again, limiting me to using the on-screen keyboard or an external one.

I tried reinstalling the Xorg tools as suggested in some forums to people with a similar issue with **sudo apt-get --purge autoremove xserver-xorg-input-all** and the respective install and trying **sudo reboot** and **sudo startx** afterwards, to no avail.

What can I do to make this work?

Some commands that helped debugging the issues to other people were

```
lspci -nnk | grep -iA3 vga

00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 530 [8086:191b] (rev 06)
    Subsystem: CLEVO/KAPOK Computer HD Graphics 530 [1558:6a01]
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller [8086:a12f] (rev 31)
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106BM [GeForce GTX 1060 Mobile 6GB] [10de:1c60] (rev a1)
    Subsystem: CLEVO/KAPOK Computer GP106BM [GeForce GTX 1060 Mobile 6GB] [1558:6a03]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

----------------------------

sudo lshw -C display

  *-display                 
       description: VGA compatible controller
       product: GP106BM [GeForce GTX 1060 Mobile 6GB]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:db000000-dbffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:e000(size=128) memory:dc000000-dc07ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: iomemory:2f0-2ef iomemory:2f0-2ef memory:2ffe000000-2ffeffffff memory:2fa0000000-2fafffffff ioport:f000(size=64) memory:c0000-dffff
```

While I was searching for solutions there was also a crash with Xorg, with the description being *Xorg assert failure: Xorg: ../../../../dix/privates.c:384: dixRegisterPrivateKey: Asserting '!global_keys[type].created' failed.* The rest of the crash report suggested some kind of problem with the NVIDIA driver.

Also, is there any way to have proper graphics switching between the Intel card and the NVIDIA one? Due to the fact that only the NVIDIA one is active all the time, the fan is always on at a very high RPM, making it very noisy, and the battery life becomes very bad. Using the Intel card for mostly everything and the NVIDIA one for CUDA things and maybe games would be ideal.

---

### Post by uRock on 2019-10-18
Moved to Installation and Upgrades per user request.

---

### Post by fernando.torres on 2020-04-21
Hi

I see that you have the same graphics card than I (Subsystem: CLEVO/KAPOK Computer GP106BM [GeForce GTX 1060 Mobile 6GB] [1558:6a03]). 

I recently tried to update the vBIOS of the graphic card but I didn't choose the right one. Also, I didn't keep a backup of the original one, so now I can't use any driver higher than 376.74.

I tried to look for a copy of the original vBIOD, but I can't find one that matches the 1558 603 subsystem, so I would appreciate it very much if you could post a backup of your graphics card's vBIOS to see if I can fix mine.

Thanks in advance.

---

