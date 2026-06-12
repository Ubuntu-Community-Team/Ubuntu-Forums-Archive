---
title: "Install from USB not booting, LUBUNTU was ok?"
date: 2020-10-11
forum: Installation &amp; Upgrades
---

### Post by bugbear6502 on 2020-10-11
After having trouble with some applications in Lubuntu 20.04.1 LTS, I decided to try the "normal" Ubuntu. I created a USB installer, using the same process I'd used for Lubuntu, and rebooted.

Despite the USB installer for Lubuntu working nicely, the USB installer for Ubuntu does not boot to a usable state.

Running it with a stopwatch, after skipping the filesystem checks, the display shows UBUNTU at the bottom, with a rotating wait-cursor-style graphic. This changes to a true (moves-with-the-mouse) wait cursor. All this is on a black screen. After 40 seconds, the screen turns to purple, and a welcome fanfare plays. The interface now shows a standard pointer-cursor.

ctrl-alt-f2 at this stage does give me a login prompt, but I'm not sure what users exist from the install USB.

In case it matters, running under the already-installed Lubuntu, "sudo lshw -class display" gives:
 [FONT=courier new]*-display                 
       description: VGA compatible controller
       product: G86M [GeForce 8400M GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:31 memory:fd000000-fdffffff memory:f4000000-f7ffffff memory:fa000000-fbffffff ioport:ef00(size=128) memory:c0000-dffff
[/FONT]
Am I doing something horribly wrong?

   BugBear

---

### Post by bugbear6502 on 2020-10-11
Initial problem solved - hold down shift key during USB boot, select "install, use SAFE graphics"

Installation now running.

EDIT; installation complete, Ubuntu 20.04.1 LTS running.

   BugBear

---

