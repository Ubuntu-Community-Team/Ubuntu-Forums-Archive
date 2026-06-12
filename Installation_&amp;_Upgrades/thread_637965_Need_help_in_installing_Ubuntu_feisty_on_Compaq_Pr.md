---
title: "Need help in installing Ubuntu feisty on Compaq Presario v3616au"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by kinngg on 2007-12-11
Hi all, I recently bought a compaq presario v3616au the specs are:

AMD Turion 64 X 2 Mobile Technology TL-60 (2.0 Ghz)
• 1GB 667 MHz / max to 4GB DDR2 Memory (512 X 2ps)
• 160 GB Hard Disk Drive
• 14.1 " TFF WXGA High Defination Widerscreen LCD Panel with BrightView Technology
• DVD +/- RW Double Layer Drive
• Wireless 802.11 a/b/g
• NVIDIA Southbridge MCP51
• Nvidia geForce Go 7150M up to 559MB Total Graphics Memory with 4096MB system memory (UMA / shared graphics)
• 2 Altec lansing branded Stereo Speakers
• Integrated 10mbps, 100 Mbps
• Integrated Bluetooth
• ExpressCard/54 Slot
• 5-in-1 integrated digital media reader slot
• 101-key compatible keyboard, Touchpad on/off button and dedicated vertical and horizontal scroll up/down pad, 1 quick lanch button

I have a live cd & installation cd for ubuntu feisty but everytime after i install when it reboots and loads again, it always get stuck on the same place for  hours, anyone know any guide for me to install ubuntu?

---

### Post by Pumalite on 2007-12-11
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by kinngg on 2007-12-11
I know how to install, thats not a problem, the problem is after installing, when I reboot it won't load, it just hangs at a place and the loading bar won't move

---

### Post by Pumalite on 2007-12-11
Unplug anything you have plugged to your computer. Be wired to the Internet during installation. See if pressing 'Esc', you can see exactly where Ubuntu gets stuck.

---

### Post by uways on 2008-01-23
> **kinngg said:**
> I know how to install, thats not a problem, the problem is after installing, when I reboot it won't load, it just hangs at a place and the loading bar won't move

I've got the exact same model (minus the RAM) and have Ubuntu 7.10 running. But I nvr got stuck at the loading screen. What does the console read? It may be that at startup Ubuntu has problems verifying certain devices

---

### Post by bwtranch on 2008-01-23
Re: #5

That shouldn't be a problem.  It'll just pass that over.

This is more basic. Do a checksum, verify the disk, look for the obvious first. Try a fresh download. Your system should be capable. Sure you're burning an iso?

---

### Post by fs3rp4 on 2008-01-23
First, look in HP site for BIOS upgrade. There is important upgrades recently.

If the upgrade don't solve your problem insert this commands in kernel boot line end:

nolapic noapic

---

