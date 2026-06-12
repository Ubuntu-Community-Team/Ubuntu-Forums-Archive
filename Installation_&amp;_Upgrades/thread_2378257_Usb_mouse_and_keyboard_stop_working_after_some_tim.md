---
title: "Usb mouse and keyboard stop working after some time..."
date: 2017-11-21
forum: Installation &amp; Upgrades
---

### Post by JoelParke on 2017-11-21
I have a logitech mouse and keyboard connected through usb.  And after sometime, the keyboard and mouse stop responding which is very annoying.  Disconnecting and reconnecting the dongle does not help.
Doing a check of dmseg, doesn't show anything obvious.  
Earlier in the timeline the  systemd-logind service dies:
```
[ +32.381459] nouveau 0000:24:00.0: gr: TRAP ch 14 [007e09d000 systemd-logind[1250]]
[  +0.000013] nouveau 0000:24:00.0: gr: GPC0/PROP trap: 00000004 [] x = 1872, y = 0, format = 0, storage type = 0
[  +0.000419] nouveau 0000:24:00.0: gr: TRAP ch 14 [007e09d000 systemd-logind[1250]]
[  +0.000008] nouveau 0000:24:00.0: gr: GPC0/TPC0/TEX: 80000041
[  +0.000004] nouveau 0000:24:00.0: gr: GPC0/TPC1/TEX: 80000041
[  +0.000004] nouveau 0000:24:00.0: gr: GPC0/TPC2/TEX: 80000041
[  +0.000004] nouveau 0000:24:00.0: gr: GPC0/TPC3/TEX: 80000041
[  +0.000004] nouveau 0000:24:00.0: gr: GPC0/TPC4/TEX: 80000000
[  +0.000011] nouveau 0000:24:00.0: fifo: read fault at 000dc9c000 engine 00 [GR] client 04 [GPC0/T1_1] reason 02 [PTE] on channel 14 [007e09d000 systemd-logind[1250]]
[  +0.000007] nouveau 0000:24:00.0: fifo: channel 14: killed
And then later I see:
[Nov21 10:33] nouveau 0000:24:00.0: Xwayland[16828]: nv50cal_space: -16
[ +14.883238] nouveau 0000:24:00.0: Xwayland[16828]: nv50cal_space: -16
[  +0.146053] nouveau 0000:24:00.0: Xwayland[16828]: nv50cal_space: -16
```
But I don't believe these are connected to the problems with the usb channel. 

How can I reset the keyboard mouse without having to reboot?  
It is a pain having to connect remotely to fix this, but not the end of the world.  Having to reboot is worse!
Any insight, help is appreciated.

Also: lsusb shows only:
```
Bus 006 Device 003: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 006 Device 002: ID 0bc2:3320 Seagate RSS LLC SRD00F2 [Expansion Desktop Drive]
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I also used a python script to reset the Logitech Unifying Receiver -- to see if that would help.  
But no help either.  
For those interested the python script (from [https://askubuntu.com/questions/645/how-do-you-reset-a-usb-device-from-the-command-line](https://askubuntu.com/questions/645/how-do-you-reset-a-usb-device-from-the-command-line)) is:
#!/usr/bin/env python
import os
import sys
from subprocess import Popen, PIPE
import fcntl
driver = sys.argv[-1]
print "resetting driver:", driver
USBDEVFS_RESET= 21780


try:
    lsusb_out = Popen("lsusb | grep -i %s"%driver, shell=True, bufsize=64, stdin=PIPE, stdout=PIPE, close_fds=True).stdout.read().strip().split()
    bus = lsusb_out[1]
    device = lsusb_out[3][:-1]
    f = open("/dev/bus/usb/%s/%s"%(bus, device), 'w', os.O_WRONLY)
    fcntl.ioctl(f, USBDEVFS_RESET, 0)
except Exception, msg:
    print "failed to reset device:", msg

---

