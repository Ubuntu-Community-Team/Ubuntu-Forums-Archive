---
title: "Raring burning CPU"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by Itiwid on 2014-01-10
Hey all.

After much faffing about I have managed to get 13.04 64bit installed on my PB easynote TE69KB. using a UNETBOOTIN flash (No dvd/cd drive)

AMD dual core e1-2500
6GB DDR3 L mem
750GB HD

rooting around online seems to bring up a fair bit of evidnce that the easynote doesn't like ubuntu very much although the CPU is on the UBUNTU tested list.

Anyway,both Coress seem to be pegged around the average of 80-90% with compiz being allegedly responsible much of the time:

itiwid@Elan:~$ top

top - 09:18:02 up 26 min,  2 users,  load average: 2,08, 2,03, 1,67
Tasks: 163 total,   4 running, 159 sleeping,   0 stopped,   0 zombie
%Cpu(s): 71,2 us, 10,2 sy,  0,0 ni, 18,2 id,  0,0 wa,  0,0 hi,  0,3 si,  0,0 st
KiB Mem:   5543728 total,  1754076 used,  3789652 free,    68680 buffers
KiB Swap:        0 total,        0 used,        0 free,   695948 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 2046 itiwid    20   0 1743m 385m  38m R  99,3  7,1  18:02.10 compiz            
 1193 root      20   0  281m  84m  17m R  31,8  1,6   6:06.27 Xorg              
 2590 itiwid    20   0  909m 257m  46m S  20,5  4,8   4:42.94 firefox           
 2584 itiwid    20   0  540m  27m  19m R   6,0  0,5   1:29.99 gnome-system-mo   
 2434 itiwid    20   0  591m  19m  12m S   4,3  0,4   0:04.76 gnome-terminal    
   28 root      20   0     0    0    0 S   0,3  0,0   0:04.43 kworker/1:1       
 2491 itiwid    20   0 26024 1604 1140 R   0,3  0,0   0:06.03 top               
 2660 root      20   0     0    0    0 S   0,3  0,0   0:03.92 kworker/0:0       
    1 root      20   0 27072 2940 1452 S   0,0  0,1   0:03.49 init              
    2 root      20   0     0    0    0 S   0,0  0,0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S   0,0  0,0   0:00.26 ksoftirqd/0       
    5 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/0:0H      
    7 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/u:0H      
    8 root      rt   0     0    0    0 S   0,0  0,0   0:00.00 migration/0       
    9 root      20   0     0    0    0 S   0,0  0,0   0:00.00 rcu_bh            
   10 root      20   0     0    0    0 S   0,0  0,0   0:01.54 rcu_sched         
   11 root      rt   0     0    0    0 S   0,0  0,0   0:00.01 watchdog/



although update-apt-xapi comes along from time to time and really rags them....

I have downloaded compmizconfig manager and turned offe bells and whistles I'm sure of (although that's not a whole lot.... know very little)

here's the output of lspci:

itiwid@Elan:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Kabini [Radeon HD 8240]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9840
00:02.0 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 0
00:02.2 PCI bridge: Advanced Micro Devices [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 5
01:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 13)
01:00.1 SD Host controller: Qualcomm Atheros Device 3010 (rev 13)
05:00.0 Network controller: Atheros Communications Inc. AR9565 Wireless Network Adapter (rev 01)

also

itiwid@Elan:~$ unity --replace
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2014-01-10 09:45:58 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Autopilot.Introspection' yet as we don't have a connection, waiting for it...
WARN  2014-01-10 09:45:58 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Unity.Debug.Logging' yet as we don't have a connection, waiting for it...
compiz (unityshell) - Error: GL_ARB_vertex_buffer_object not supported

compiz (core) - Error: Plugin initScreen failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0x3800062
  Serial number of failed request:  9269
  Current serial number in output stream:  9269
itiwid@Elan:~$ 

found other people with similar issues... is this a bug or am i misssing drivers or something?
any help would be much appreciated.


Thanks.

G

---

