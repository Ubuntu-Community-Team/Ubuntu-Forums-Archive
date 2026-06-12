---
title: "Several pbs when Installing 15.10 on an MSI ghost pro 4k GS60 6QE-036"
date: 2015-12-16
forum: Installation &amp; Upgrades
---

### Post by SouheilBs on 2015-12-16
I am posting the dmesg and lspci outputs for more details!
Many thanks for any advice

---

### Post by ian-weisser on 2015-12-16
Perhaps you could take a moment and describe the problem you are seeing?
It will help us know what to look for in those large, long, tedious logs.

---

### Post by SouheilBs on 2015-12-17
Sure Iain

As I am not an ubuntu expert I thought it might be easier for you to spot it from the logs ;)
Mainly from what I understood so far from my long browsing and googling:
both graphics the intel and the nvidia ones are not working properly
I have to put nomodeset at the grub for the system to start
I was also putting i915.preliminary_hw_support=1 at the grub but this didn't make any difference either
I also had to make some change for the wireless network to be usable (see: [http://ubuntuforums.org/showthread.php?t=2301100&p=13382344#post13382344](http://ubuntuforums.org/showthread.php?t=2301100&p=13382344#post13382344) )
The bluetooth is still not working.
I also upgraded to kernel 4.3.2-040302 and still the same problems.
the resolution is really bad and fixed to 800x2600 without any option to change it.
I also tried to clean and reinstall the nvidia driver without success.
yesterday I tried the current 16.04 Xenial xerus and still the same problem exept for thr wireless network.

Below are few more logs:
ubuntu-drivers devices
```
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free

== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd000013D8sv00001462sd00001158bc03sc02i00
model    : GM204M [GeForce GTX 970M]
vendor   : NVIDIA Corporation
driver   : nvidia-352 - distro non-free recommended
driver   : nvidia-352-updates - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin


=========================
xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected primary 800x600+0+0 0mm x 0mm
   800x600       75.00* 
==================================
glxinfo
name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
================================================
 lspci -nnk | grep "VGA\|'Kern'\|3D\|Display"
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:191b] (rev 06)
01:00.0 3D controller [0302]: NVIDIA Corporation GM204M [GeForce GTX 970M] [10de:13d8] (rev a1)

==============================
```

I know this might be a mix of many thing but it is really frustrating not to get such machine work properly with the best os

Thanks

one more log for the bluetooth
```
dmesg |grep -i bluetooth
[    6.170724] Bluetooth: Core ver 2.20
[    6.170757] Bluetooth: HCI device and connection manager initialized
[    6.170764] Bluetooth: HCI socket layer initialized
[    6.170769] Bluetooth: L2CAP socket layer initialized
[    6.170779] Bluetooth: SCO socket layer initialized
[    6.480136] Bluetooth: HCI UART driver ver 2.3
[    6.480145] Bluetooth: HCI UART protocol H4 registered
[    6.480150] Bluetooth: HCI UART protocol BCSP registered
[    6.480155] Bluetooth: HCI UART protocol LL registered
[    6.480159] Bluetooth: HCI UART protocol ATH3K registered
[    6.480164] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    6.480237] Bluetooth: HCI UART protocol Intel registered
[    6.480282] Bluetooth: HCI UART protocol BCM registered
[    6.480286] Bluetooth: HCI UART protocol QCA registered
[    7.640150] Bluetooth: Patch file not found ar3k/AthrBT_0x00000200.dfu
[    7.640842] Bluetooth: Loading patch file failed
[   13.658366] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.658368] Bluetooth: BNEP filters: protocol multicast
[   13.658370] Bluetooth: BNEP socket layer initialized
```

---

### Post by SouheilBs on 2015-12-19
I wonder if anyone had similar problems/solutions?
Thanks

---

