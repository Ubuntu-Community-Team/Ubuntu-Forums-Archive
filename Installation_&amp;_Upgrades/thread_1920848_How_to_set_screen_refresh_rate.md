---
title: "How to set screen refresh rate ?"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by gmd3006 on 2012-02-05
I have a Dell Dimension / Celeron D PC, with Windows XP, and 3  80GB hard disks.  This is my first foray into Linux ever.  In Dec. '11 I downloaded Ubuntu 11.10 to a USB, and installed from there.  I partitioned sda with 2 partitions for XP,  sdb with 3 partitions for Ubuntu, and left sdc with 1 ntfs partition for music .mp3 files.  I'm using the default gnome GUI, mostly.  I now have a dual-boot XP or Ubuntu machine!

Almost everything worked right off the bat.  I can go into system settings and change the screen resolution, and find that 1024x768 works best for my CRT, just like it used to do in XP.  However, the default 60 Hz refresh rate is annoyingly flickery.  In XP, I could reset the display refresh rate to 70 Hz, but refresh rate is not offered as a selection in Ubuntu's system settings menus.

Here is my video card info:
lshw -c display
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff ioport:ed98(size=8)

gary@gary-Dell-DE051:~$ **xrandr**
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1280x1024      59.9 +
  ** 1024x768       85.0     75.1     60.0* **
   800x600       100.0     85.1     75.0     60.3  
   640x480        85.0     60.0  
   720x400        70.1  

I do not have an xorg.conf file anywhere in my file system.

I surmise from this that I should be able to reset to **75.1** Hz at 1024x768.  How do I configure Ubuntu to do so?

Thanx!!

---

### Post by dino99 on 2012-02-05
the actual kernel directly deals with hardware detection & settings, so you dont have xorg.conf

but it can be set:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by gmd3006 on 2012-02-05
dino99, the reference you linked indicated that xrandr could be used to reset the refresh rate, so I used the command as directed, and it did change the rate.  It demonstrated that Ubuntu wouldn't choke on the new setting.  The article also seemed to indicate that the new setting would last only for the "current session".  I exited my terminal, then reopened a new terminal, and xrandr showed that the refresh rate stayed at 75.1  I didn't reboot to test that though.

The reference also suggested that the file ~/.config.monitors.xml contains the resolution & refresh parameters.  I edited the refresh rate from 60 to 75.1 in that file, and then rebooted.  Rerunning xrandr showed that the revised refresh rate *did* stick through the rebooting.  And, my eyes show that the screen's flickering is gone.

Thanx for the help!

---

