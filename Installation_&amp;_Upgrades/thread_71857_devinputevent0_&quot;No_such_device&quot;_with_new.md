---
title: "/dev/input/event0 &quot;No such device&quot; with new kernel"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by dishbert on 2005-10-04
I;ve been running VDR on Ubuntu and a vanilla 2.6.10-rc2 kernel for about a year.  New VDR software needs the new 2.6.14-rc2 kernel, but when I installed and booted into it, VDR gives the  "/dev/input/event0 "No such device" on the TV screen, and the floppy drive tries to mount.  The drive clunks away, and once a floppy is inserted it mounts the drive.  I used my old 2.6.10 menuconfig to build the new kernel.
I checked and "event interface" is selected to load as a module. I rebooted into the old 2.6.10-rc2 kernel, and VDR stilll loads fine there.   In the new kernel running dmesg after trying to start VDR produces about 50 lines of:  "end_request: I/O error, dev fd0, sector 0."
I don't see anything like evdev in the lsmod output.  
I now remember I used a script I found on a Ubuntu forum (or maybe in the wiki) to load my Windoze partition automatically at startup. This worked fine loaded on top of my 2.6.10 kernel, but it may be upsetting the new one.
I've searched through the forums and the wiki, but I can't find the script I used (it's been many months).
Any ideas how I can reverse this?

---

