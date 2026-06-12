---
title: "Audio and video failed after update"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by rroberto on 2008-05-02
Hi,

I have been using Ubuntu for some time now and I'm loving it. I started using 7.10 then recently upgraded to 8.04. Everything was fine until I downloaded and installed some updates but I'm not sure which of the updates caused my video and sound to crash. Below are the packages I updated before the crash. I would really appreciate if someone can point me to the right direction.

Currently I'm logged on using the generic kernel from the Grub menu and everything seems to be working fine. But when I boot to the RT Kernel which is the default option, nothing basically works. My resolution is too low, and my NVIDIA Drivers are gone also my sound card can't be detected as well.

Can someone please help and maybe identify which package I installed that caused these failures, maybe I can try and remove them from Synaptic and hopefully I'll get my system back up again.

Thank you in advance and thumbs up for a great alternative to Microsoft.

rroberto



*************************
Updates before hardware failure
*************************

Commit Log for Thu May  1 21:24:32 2008


Upgraded the following packages:
bsdutils (1:2.13.1-5ubuntu1) to 1:2.13.1-5ubuntu2
evolution (2.22.1-0ubuntu3) to 2.22.1-0ubuntu3.1
evolution-common (2.22.1-0ubuntu3) to 2.22.1-0ubuntu3.1
evolution-data-server (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
evolution-data-server-common (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
evolution-plugins (2.22.1-0ubuntu3) to 2.22.1-0ubuntu3.1
gnome-system-monitor (2.22.0-1ubuntu3) to 2.22.1-0ubuntu1
libcamel1.2-11 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libebook1.2-9 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libecal1.2-7 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libedata-book1.2-2 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libedata-cal1.2-6 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libedataserver1.2-9 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libedataserverui1.2-8 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libegroupwise1.2-13 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libexchange-storage1.2-3 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libgdata-google1.2-1 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libgdata1.2-1 (2.22.1-0ubuntu2) to 2.22.1-0ubuntu2.1
libldap-2.4-2 (2.4.7-6ubuntu3) to 2.4.7-6ubuntu4.1
mount (2.13.1-5ubuntu1) to 2.13.1-5ubuntu2
update-manager (1:0.87.24) to 1:0.87.25
update-manager-core (1:0.87.24) to 1:0.87.25
util-linux (2.13.1-5ubuntu1) to 2.13.1-5ubuntu2
util-linux-locales (2.13.1-5ubuntu1) to 2.13.1-5ubuntu2
wine (0.9.59-0ubuntu4) to 0.9.59-0ubuntu5

Installed the following packages:
lib32nss-mdns (0.10-3ubuntu2)

***************************
Below is my hardware information, I hope it helps.
***************************

I'm running AMD Atlon64 3800+ with 2GB RAM on an ASUS A8V Deluxe, also using NVDIA 7300GT with 2 LCD monitors.

  Device: "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:10.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: usbcore is active
    Driver Activation Cmd: "modprobe usbcore"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (USB Controller)

62: ADB 00.0: 10502 Bus Mouse
  [Created at input.159]
  UDI: /org/freedesktop/Hal/devices/computer_logicaldev_input
  Unique ID: kZYT.9XB1QYZ8Aa7
  Hardware Class: mouse
  Model: "Apple Macintosh mouse button emulation"
  Vendor: int 0x0100 "Apple"
  Device: int 0x0300 "Macintosh mouse button emulation"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event0
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

63: PS/2 00.0: 10800 Keyboard
  [Created at input.139]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input
  Unique ID: EXC1.TBWTwSuMeW2
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: int 0x0211 
  Device: int 0x0001 "AT Translated Set 2 keyboard"
  Device File: /dev/input/event1
  Device Files: /dev/input/event1, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:65
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

64: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.159]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
  Unique ID: AH6Q.zl07e6mUyw1
  Hardware Class: mouse
  Model: "ImExPS/2 Generic Explorer Mouse"
  Vendor: int 0x0210 
  Device: int 0x0025 "ImExPS/2 Generic Explorer Mouse"
  Device File: /dev/input/mice (/dev/input/mouse2)
  Device Files: /dev/input/mice, /dev/input/mouse2, /dev/input/event7, /dev/input/by-path/platform-i8042-serio-1-event-mouse, /dev/input/by-path/platform-i8042-serio-1-mouse
  Device Number: char 13:63 (char 13:34)
  Driver Info #0:
    Buttons: 5
    Wheels: 2
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

65: None 00.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: X86-64
  Vendor: "AuthenticAMD"
  Model: 15.47.2 "AMD Athlon(tm) 64 Processor 3800+"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,syscall,nx,mmxext,fxsr_opt,lm,3dnowext,3dnow,up,rep_good,pni,lahf_lm
  Clock: 1000 MHz
  BogoMips: 2006.89
  Cache: 512 kb
  Config Status: cfg=new, avail=yes, need=no, active=unknown

66: None 00.0: 10701 Ethernet
  [Created at net.125]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.ku_pZL9tQC3
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:0a.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "skge"
  Driver Modules: "skge"
  Device File: eth0
  HW Address: 00:11:2f:ba:bd:2a
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (Ethernet controller)

67: None 00.0: 10700 Loopback
  [Created at net.125]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by rroberto on 2008-05-05
It's me again. I just want to update my post as everything is all good now. For a while I was using the generic kernel but I have recently did some updates a few days ago and to my surprise my RT kernel is up and running again after booting on it this morning.

So, to anyone who was on the same boat as me everything will be ok. Just stick with it and help will come along.

---

