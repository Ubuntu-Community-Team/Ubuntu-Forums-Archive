---
title: "Unable to install, not detecting harddrive"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by RvGaTe on 2007-10-19
Hello,

After successfully installing winXP on my system, i wanted to go for a dual boot with Ubuntu...

After booting up using the live cd, and starting the installation, everything works fine... Untill it reaches the Partitioner... telling me there is no device.

Here are my specs;

Motherboard: Abit IP35-E
HDD: Western Digital Caviar SE 200gb 7200rpm S-ATA

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 13)
05:03.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

```

```

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.

```

It's also not displayed in the device manager... I'm like... completely lost in how to solve this problem... and if any of you experience the same problem, or even better, know how to fix this... please let me know...

Thx in advance

Rv

---

### Post by RvGaTe on 2007-10-19
bump :)

---

### Post by RvGaTe on 2007-10-20
bump2 :(

---

### Post by Bultot on 2007-10-23
bump3

---

### Post by Soybean on 2007-10-23
That's pretty weird. I don't know what could be causing it, but I've got a couple of suggestions:

1) I have a P35 board too, although mine's by Gigabyte. One of the extra features Gigabyte built in was a couple of extra SATA ports... so there are a bunch of yellow/orange SATA ports on the board (the standard Intel-controlled ones), and then a couple of purple ones (handled by a special Gigabyte controller). If your board has anything like that, I recommend you try using the standard Intel ports.

2) Check your BIOS for any weird hard drive related settings. RAID should be off, SATA should be on... for anything else, you may need to look it up to find out what it is. There's lots of weird stuff in there these days.

Beyond that, I haven't got much. Oh! You could look through the logs on the live CD -- I suspect it has a similar log structure to a regular Linux system, in /var/log. You can try skimming through "messages" and "syslog" and maybe some others... if you can find an error related to your hard drive, then you've got something you can google. :)

Sorry I can't be more helpful here... SATA drives tend to 'just work', so I don't have much experience troubleshooting them. Good luck!

---

### Post by RvGaTe on 2007-11-01
Sorry for the late reply to my own post, 

For some reason, after deciding to attach my normal IDE drive back in, it seemed to recognize both SATA and IDE drives...

To make sure it keeps working, i installed ubuntu on my IDE drive, and leave Windows XP on my SATA drive... Tho the installer did allow me to install it on the SATA.

Wich makes me think tho... why would spontaniously detect my sata when he has an ide companion...?

---

### Post by Soybean on 2007-11-02
Hmm... well, it shouldn't matter, generally.

One possibility, though, is that your BIOS was still configured for the old IDE drive. In this situation, Ubuntu might get confused, since the BIOS would report that there was an IDE drive, when there obviously isn't. This actually happened to me with the floppy IDE channel... my BIOS had the floppy drive enabled, but I didn't actually have a floppy drive. Windows didn't even notice, but Ubuntu wouldn't boot because it was trying to set up drivers for this imaginary floppy drive.

Or, it could be some other strange phenomenon... it's good that you found a workaround, though! :)

---

### Post by tk421 on 2007-11-03
I am having the same problem at samsung q35. Unable to find a solution. I have checked BIOS nothing wrong was found.

---

