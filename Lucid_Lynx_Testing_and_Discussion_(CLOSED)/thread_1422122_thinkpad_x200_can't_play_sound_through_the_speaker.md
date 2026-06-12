---
title: "thinkpad x200 can't play sound through the speakers,but work ok through headphones,a"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by feiy on 2010-03-05
Binary package hint: pulseaudio

thinkpad x200 can't play sound through the speakers,but work ok when the headphones are unplugged,after updated 3.4

feiy@feiy-laptop:~$ cat /etc/issue
Ubuntu lucid (development branch) \n \l
feiy@feiy-laptop:~$ uname -a
Linux feiy-laptop 2.6.33-020633-generic #020633 SMP Thu Feb 25 10:10:03 UTC 2010 x86_64 GNU/Linux
i had try the 2.6.32 kernel,it's fail too!
feiy@feiy-laptop:~$ lspci
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
feiy@feiy-laptop:~$ lshw
*-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:30 memory:f2620000-f2623fff

ProblemType: Bug
AlsaVersion: Advanced Linux Sound Architecture Driver Version 1.0.21.
Architecture: amd64
ArecordDevices:
 **** List of CAPTURE Hardware Devices ****
 card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
   Subdevices: 1/1
   Subdevice #0: subdevice #0
AudioDevicesInUse:
 USER PID ACCESS COMMAND
 /dev/snd/controlC0: feiy 4124 F.... pulseaudio
 /dev/snd/pcmC0D0p: feiy 4124 F...m pulseaudio
Card0.Amixer.info:
 Card hw:0 'Intel'/'HDA Intel at 0xf2620000 irq 30'
   Mixer name : 'Conexant CX20561 (Hermosa)'
   Components : 'HDA:14f15051,17aa20ff,00100000'
   Controls : 14
   Simple ctrls : 7
Card29.Amixer.info:
 Card hw:29 'ThinkPadEC'/'ThinkPad Console Audio Control at EC reg 0x30, fw 7XHT22WW-1.04'
   Mixer name : 'ThinkPad EC 7XHT22WW-1.04'
   Components : ''
   Controls : 1
   Simple ctrls : 1
Card29.Amixer.values:
 Simple mixer control 'Console',0
   Capabilities: pswitch pswitch-joined penum
   Playback channels: Mono
   Mono: Playback [on]
Date: Fri Mar 5 09:03:22 2010
DistroRelease: Ubuntu 10.04
ExecutablePath: /usr/bin/pulseaudio
InstallationMedia: Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
Package: pulseaudio 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu11
ProcEnviron:
 LANGUAGE=zh_CN:zh
 PATH=(custom, user)
 LANG=zh_CN.utf8
 SHELL=/bin/bash
SourcePackage: pulseaudio
Uname: Linux 2.6.33-020633-generic x86_64

i had install the linux-alsa-driver-modules-2.6.32-15-generic and switch back to the official kerne 2.6.32-15-generic,but the bug too! no sound through the speakers

the bug report url:[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/532352](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/532352)

---

### Post by feiy on 2010-03-05
who can help me ?

---

### Post by godhika on 2010-03-05
Check preferences-> sound -> output if the option connector is set to analog output or analog headphones. If thats the case set it to analog speakers. Hope that helps

---

### Post by Yellow Pasque on 2010-03-05
> thinkpad x200 can't play sound through the speakers,but work ok when the headphones are unplugged
So the speakers play when the headphones are unplugged and then they don't play when you plug in the headphones? That's how it's supposed to work

---

### Post by blakamin on 2010-03-05
mine has the problem with turning the speakers down every reboot.
alt-f2 run *gnome-alsamixer* or *alsamixer* in terminal and try turning your speakers up.

---

### Post by feiy on 2010-03-06
this is the sound set,and gnome-alsamixer set
sorry,the bug info:
thinkpad x200 can't play sound through the speakers,but work ok when the
headphones are plugged,after updated 3.4

---

### Post by feiy on 2010-03-06
sudo alsamixer screenshot

---

