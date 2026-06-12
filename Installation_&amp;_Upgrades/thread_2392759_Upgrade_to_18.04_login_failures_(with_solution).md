---
title: "Upgrade to 18.04 login failures (with solution)"
date: 2018-05-24
forum: Installation &amp; Upgrades
---

### Post by rwalkerIII on 2018-05-24
After an automated distro upgrade from Ubuntu 17.10 to Ubuntu 18.04 (Bionic Beaver), I could no longer login on the display manager prompt after the subsequent reboot.  I was unable to find a solution online, but was able to fix it myself and wanted to share it here.

My configuration relevant to this problem:
root@walkubu:~# lshw -c video
  *-display                 
       description: VGA compatible controller
       product: GM206 [GeForce GTX 960]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:131 memory:ee000000-eeffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:c0000-dffff


The Problem:
1. The software upgrade manager prompted me with an upgrade to 18.04.  I accepted and upgrade went in clean.
2. The display manager login prompt came up, I entered my password, and after a few seconds it prompted me for the password again.
3. The syslog showed this:
      May 24 18:55:38 walkubu gnome-session[3392]: No protocol specified
      May 24 18:55:38 walkubu gnome-session[3392]: Unable to init server: Could not connect: Connection refused 
      May 24 18:55:38 walkubu gnome-session-c[3487]: cannot open display: :2
      May 24 18:55:38 walkubu gnome-session[3392]: No protocol specified
      May 24 18:55:38 walkubu gnome-session[3392]: Unable to init server: Could not connect: Connection refused
      May 24 18:55:38 walkubu gnome-session-c[3488]: cannot open display: :2
      May 24 18:55:38 walkubu gnome-session[3392]: gnome-session-binary[3392]: WARNING: software acceleration check failed: Child process exited with code 1   
      May 24 18:55:38 walkubu gnome-session[3392]: gnome-session-binary[3392]: CRITICAL: We failed, but the fail whale is dead. Sorry....
      May 24 18:55:38 walkubu gnome-session-binary[3392]: WARNING: software acceleration check failed: Child process exited with code 1
      May 24 18:55:38 walkubu gnome-session-binary[3392]: CRITICAL: We failed, but the fail whale is dead. Sorry....
      May 24 18:55:38 walkubu gdm-x-session: session exited with status 1

Wasn't sure if that was *the* problem, but it led me to believe it was a display manager issue.  (Also I came to this conclusion after trying Xserver instead of Wayland, which didn't change anything.)

Solution:
0. Found I had the Nvidia driver running, which I didn't want because I'm running Wayland.
       sudo lshw -c video
1. I removed the Nvidia drivers to force Nouveau to run:
          sudo apt-get purge nvidia*
2. Rebooted
3. installed lightdm because I suspected gdm3 was the issue
          sudo apt-get install lightdm
4. stopped gdm
          sudo service gdm stop
5. started lightdm
          sudo service lightdm
6. On the login screen, made lightdm the default from dropdown menu

Then I was able to login successfully.  Hope this is helpful.

---

