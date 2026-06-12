---
title: "mutiple HARD crashes on 14.04 LTS new install"
date: 2014-05-27
forum: Installation &amp; Upgrades
---

### Post by linuxgrrl on 2014-05-27
hi, 
I used 12.10 for years and had some problems but nothing like this.
After a clean install of 14.04 LTS, i am experiencing multiple HARD crashes where the mouse pointer moves but everything (everything) else is completely not responsive, including running instances of top and system monitors that cease scrolling.

These crashes have happened at shutdown, when starting basic stuff like gmail, listening to music on banshee and other random times.

I'm so proud i learned the magic REISUB key combo for hard re-boot, but I wish i didn't need to use is 2x daily. What could be the problem?  It's the same hardware that was running 12.10 adequately just a couple of days ago, so i'm pretty sure it's not the hardware.
Thanks
Mary

---

### Post by fantab on 2014-05-27
You must give more details about your machine's hardware specifications, otherwise it will be difficult to help you.
Is there any other OS in the picture? What OS?
Does your machine use BIOS or is it new enough to have UEFI?
Checking logs for errors and warnings is an excellent idea... look in /var/logs for 'boot.log', 'dmesg', kern.log etc...
If you find any 'errors', 'warnings', or 'failed' messages then post them here telling us what 'log' they are from. 
When you paste the messages please use code tags to warp them.

---

### Post by ubfan1 on 2014-05-28
When "top" is running when the problem occurs, is any process at 100%+ cpu? (like compiz).  Can you still switch to a virtual terminal (Ctrl-Alt-F2).  Can you run top there?  If you run ps to find the lightdm session, and you kill it, do things return to a normal login screen?  Did you run the software updates after the install?  Does this happen in recovery mode?...

---

### Post by linuxgrrl on 2014-05-28
Thanks so much, here are details:
AMD Phenom II X3 720 Processor 64 bit, reported temp 79-88 degrees F
Onboard graphics and sound
some kind of nice motherboard with extra durable copper layer, it's about 3 years old so no UEFI
No other OS involved. /home, /photos, and /music are on their own partitions.  Fresh install of 14.04LTS on the / partition. Have installed banshee, wine, proprietary codecs and some applets.

boot.log has no error messages although sometimes at boot i get the 'crash report detected' message. it wont' link to a message or details, the crash report itself will freeze
top looked completely normally the time it was open during a crash (nothing over 15% CPU)
Could not switch to a terminal during crash

Warnings clipped from dmesg
```
[   16.235707] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x096080c1
[   16.235709] nouveau  [  DEVICE][0000:01:00.0] Chipset: G96 (NV96)
[   16.235710] nouveau  [  DEVICE][0000:01:00.0] Family : NV50
[   16.236300] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[   16.266757] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20131115/utaddress-251)
[   16.266764] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.268029] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   16.272226] sp5100_tco: PCI Revision ID: 0x3c
[   16.272253] sp5100_tco: failed to find MMIO address, giving up.
[   16.280492] Linux video capture interface: v2.00
[   16.288378] MCE: In-kernel MCE decoding enabled.

[    2.694680] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.728577] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    2.728579] i8042: If AUX port is really absent please use the 'i8042.noaux' option


[   16.272253] sp5100_tco: failed to find MMIO address, giving up.

```
several messages like these in kernlog
```
May 25 20:34:23 mythbox kernel: [   10.552224] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20131115/utaddress-251)
```

---

### Post by ubfan1 on 2014-05-28
Did you run the software updater on the system after the install?  That might fix some things.  You might check the BIOS settings about ACPI and see if there is anything to toggle.  There are several kernel boot options for acpi settings:
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic
try adding on the grub.cfg linux line before the "quiet splash" near the end.

---

### Post by linuxgrrl on 2014-05-29
I did run the software updater, at the beginning. Will try the acpi stuff tonite and report back.

---

### Post by linuxgrrl on 2014-05-31
OK, so ACPI was a clue. The upgrade had changed a power management setting to put the computer to sleep after an hour of inactivity. Suspend was crashing the machine everytime I got up for an hour or more. It doesn't explain the crashes while working, but many are sorted out now thanks!

Now, if someone could just explain why every Ubuntu version I have ever tried (loyal user for about 8 years), sleep and suspend NEVER work and ALWAYS cause the machine to crash.  My bios settings look sensible; i've done a little reading about ACPI but it seems hopeless that a normal user (average intelligence like me) could ever get it to work.

When i run ACPI diagnostics, i get some message like "please check that your kernel is enabled for ACPI" but I''ve no idea how to check or what to fix. My kernel is whatever ubuntu provides for a 64 bit machine.

---

