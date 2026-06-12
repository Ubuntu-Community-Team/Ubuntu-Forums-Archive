---
title: "40-second boot delay: is it udev?"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by adpads on 2011-02-03
Hi all!
This morning I had the courage to run an apt-get autoremove which took some 275 packages off my hard drive, and now I am experiencing a delay of about 40 seconds at boot, after grub, before the plymouth splash appears. The cursor blinks on a black screen while the hard drive churns away. Finally two error messages appear too quickly to be read, and then the bootsplash kicks in.

I can find the instant in the dmesg where the delay happens, but can't locate the cause.

Here's what my dmesg looks like:

[    1.623822]  sda:
[    1.663176] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.671312]  sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.732537] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.832372] hub 2-1:1.0: USB hub found
[    1.832472] hub 2-1:1.0: 8 ports detected
[    2.111203] usb 2-1.5: new high speed USB device using ehci_hcd and address 3
[    2.652134] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   41.561639] udev[481]: starting version 163
[   41.575207] lp: driver loaded but no devices found
[   41.610484] Adding 4200960k swap on /dev/sda6.  Priority:-1 extents:1 across:4200960k 
[   41.684133] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[   41.685517] agpgart-intel 0000:00:00.0: detected 131068K stolen memory, trimming to 32768K
[   41.737571] acer-wmi: Acer Laptop ACPI-WMI Extras
[   41.737799] acer-wmi: Unable to detect available WMID devices

The laptop is an Acer Timeline X 3820TG, with the dual GPU "switchable graphics." These dual graphics cards have given me enough trouble in the past that I wouldn't be surprised if they were the problem. But the hard drive action sounds like a 'fsck,' and seems to be contemporaneous with the dmesg notice that the root partition is mounted.

Incidentally, my boot wasn't all that fast before; I would not be surprised if this delay was preexisting, but used to happen after the plymouth boot screen was already on screen. Still, if I can get rid of this one ugly delay, I can have a fast (c. 10 secs) boot time.

How can I locate this problem?

---

### Post by claretsfan on 2011-02-03
adpads

Got something similar here, I think.  I was just about to post my problem when I found your post.

Here's the relevant bit of dmesg:

[    2.640169] firewire_core: created device fw0: GUID 000461000005ff4b, S400
[    8.487651] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[   29.651256] Adding 1076316k swap on /dev/sdb9.  Priority:-1 extents:1 across:1076316k 
[   30.264936] udev[443]: starting version 163

Plymouth starts up, then nothing appears to happen for a long time.  Boot used to take about 40 seconds to the desktop, now it's over 60 seconds.  Other than the usual updates, I've not installed anything that I can recall, or changed any setting.

I've attached the bootchart, which I confess is beyond me.

I'll keep searching and experimenting, but thanks in advance for any help!

---

### Post by claretsfan on 2011-02-03
Same problem here (but no solution):

[http://ohioloco.ubuntuforums.org/showthread.php?p=10199760](http://ohioloco.ubuntuforums.org/showthread.php?p=10199760)

---

### Post by adpads on 2011-02-04
OK guys - I got it, at least partially.

I managed to eliminate the 40-second delay, though I am still getting the error messages, which seem to be related to something else.

The culprit for the delay is ureadahead; the remedy is: 1) reinstall ureadahead (and its dependencies) with synaptic; reboot; delete the file /var/lib/ureadahead/pack; reboot again; on this first reboot ureadahead will be reprofiled; after that it should function normally.

I hope that helps! I'll be travelling for a week and won't have this computer with me, will try to sort out the other error I'm getting ("acer-wmi: Unable to detect available WMID devices") when I get back.

---

### Post by claretsfan on 2011-02-04
Yep- that's certainly fixed the ureadahead problem- thanks!

I've rebooted 3 times, just to check.

Good luck with the other problem.  I'll let the folks on the other thread I linked to know of your solution to this one.

---

### Post by adpads on 2011-02-04
ok, but a word of warning - I just rebooted and had a 40-second delay again, so I think I may have spoken too soon. Apparently I've located the problem, but I haven't yet found whatever it is that's messing up the ureadahead profiling. And I have a suspicion that that may be something different for each of us.. time will tell!

---

### Post by claretsfan on 2011-02-04
Sadly, you're right adpads.  Reboot number 4 got me back to:

[    2.688147] firewire_core: created device fw0: GUID 000461000005ff4b, S400
[    8.630584] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[   29.848350] Adding 1076316k swap on /dev/sdb9.  Priority:-1 extents:1 across:1076316k 
[   30.455684] udev[426]: starting version 163

21 second delay.

I tried an apt-get purge ureadahead instead of using synaptic, but no joy.

I tried running without ureadahead- no 20 second delay, but overall boot was slower.

Back to the drawing board.

---

