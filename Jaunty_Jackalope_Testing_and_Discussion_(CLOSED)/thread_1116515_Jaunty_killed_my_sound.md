---
title: "Jaunty killed my sound"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by alexb2 on 2009-04-05
I upgraded to Jaunty this afternoon, looks like everything except the sound is working.  Anyone else got this working on a 82801H / Dell 1420n?

Here is output from hwinfo --sound:

```
alex@entropy:~$ hwinfo --sound
27: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_284b
  Unique ID: u1Nb.wUq5O6bR3r1
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Dell Inspiron 1420"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x284b "82801H (ICH8 Family) HD Audio Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x01f3 "Inspiron 1420"
  Revision: 0x02
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe9fc000-0xfe9fffff (rw,non-prefetchable)
  IRQ: 21 (21182 events)
  Module Alias: "pci:v00008086d0000284Bsv00001028sd000001F3bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

And pulseaudio -vvv --check:

```
alex@entropy:~$ pulseaudio -vvv --check
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
I: main.c: Daemon running as PID 13014
```

---

