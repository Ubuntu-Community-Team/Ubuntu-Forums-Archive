---
title: "Desktop Immediately Wakes from Suspend"
date: 2018-02-25
forum: MINT
---

### Post by bug67 on 2018-02-25
I've already posted this problem on [Linux Mint Forums]("https://forums.linuxmint.com/viewtopic.php?f=49&t=263000") and have reached a stalemate there.  It would be super awesome to somehow figure out what's keeping this machine from staying suspended.  So, I'll try to give all the pertinent info here as well in the hopes of resolving this issue.

The machine in question is a Dell T1600 Workstation I was given by my wife.  It has really good specs for what it is and was a huge improvement over what I had.  I installed Linux Mint 18.3 with the Latest BIOS set up in Legacy mode.  Here is some machine info:

~ $ inxi -Fxz

```
System:    Host: LillyDell-T1600 Kernel: 4.13.0-36-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.6.7 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Linux Mint 18.3 Sylvia
Machine:   System: Dell product: Precision T1600 v: 01
           Mobo: Dell model: 06NWYK v: A01 Bios: Dell v: A17 date: 05/07/2017
CPU:       Quad core Intel Xeon E31270 (-HT-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 27138
           clock speeds: max: 3800 MHz 1: 3392 MHz 2: 3392 MHz 3: 3392 MHz
           4: 3392 MHz 5: 3392 MHz 6: 3392 MHz 7: 3392 MHz 8: 3392 MHz
Graphics:  Card: NVIDIA GF108 [GeForce GT 730] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1200@59.95hz, 1920x1200@59.94hz
           GLX Renderer: GeForce GT 730/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 384.111 Direct Rendering: Yes
Audio:     Card-1 NVIDIA GF108 High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 C-Media CMI8788 [Oxygen HD Audio]
           driver: snd_oxygen port: 2000 bus-ID: 04:04.0
           Card-3 Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-4 Microsoft LifeCam Cinema driver: USB Audio usb-ID: 003-007
           Sound: Advanced Linux Sound Architecture v: k4.13.0-36-generic
Network:   Card: Intel 82579LM Gigabit Network Connection
           driver: e1000e v: 3.2.6-k port: 4040 bus-ID: 00:19.0
           IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1250.3GB (6.1% used)
           ID-1: /dev/sda model: INTEL_SSDSC2MH25 size: 250.1GB
           ID-2: /dev/sdb model: WDC_WD1002FAEX size: 1000.2GB
Partition: ID-1: / size: 214G used: 12G (6%) fs: ext4 dev: /dev/sda1
           ID-2: /home size: 917G used: 44G (6%) fs: ext4 dev: /dev/sdb1
           ID-3: swap-1 size: 17.13GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: N/A gpu: 0.0:51C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 245 Uptime: 1:54 Memory: 1573.6/15996.6MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35
``` 

**_Logs upon resume from sleep_**:

"cat /var/log/syslog"  returns:

```
Feb 19 17:43:11 LillyDell-T1600 kernel: [ 3546.575970] [UFW BLOCK] IN=eno1 OUT= MAC=5c:f9:dd:70:14:07:54:88:0e:b3:d2:b4:08:00 SRC=10.0.1.52 DST=10.0.1.64 LEN=359 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59072 DPT=52820 LEN=339 
Feb 19 17:43:11 LillyDell-T1600 kernel: [ 3546.578992] [UFW BLOCK] IN=eno1 OUT= MAC=5c:f9:dd:70:14:07:90:f1:aa:f1:bb:a6:08:00 SRC=10.0.1.57 DST=10.0.1.64 LEN=319 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=52820 LEN=299 
Feb 19 17:43:12 LillyDell-T1600 kernel: [ 3547.219540] [UFW BLOCK] IN=eno1 OUT= MAC=5c:f9:dd:70:14:07:68:54:fd:31:2d:10:08:00 SRC=10.0.1.27 DST=10.0.1.64 LEN=344 TOS=0x00 PREC=0x00 TTL=64 ID=19380 DF PROTO=UDP SPT=49415 DPT=52820 LEN=324 
Feb 19 17:43:12 LillyDell-T1600 kernel: [ 3547.220040] [UFW BLOCK] IN=eno1 OUT= MAC=5c:f9:dd:70:14:07:68:54:fd:31:2d:10:08:00 SRC=192.168.49.1 DST=10.0.1.64 LEN=344 TOS=0x00 PREC=0x00 TTL=64 ID=333 DF PROTO=UDP SPT=34609 DPT=52820 LEN=324 
Feb 19 17:43:12 LillyDell-T1600 kernel: [ 3547.423473] [UFW BLOCK] IN=eno1 OUT= MAC=5c:f9:dd:70:14:07:00:bb:3a:db:02:fa:08:00 SRC=10.0.1.7 DST=10.0.1.64 LEN=359 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55221 DPT=52820 LEN=339 
Feb 19 17:43:12 LillyDell-T1600 kernel: [ 3547.802341] [UFW BLOCK] IN=eno1 OUT= MAC=5c:f9:dd:70:14:07:90:f1:aa:f1:bb:a6:08:00 SRC=10.0.1.57 DST=10.0.1.64 LEN=319 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=52820 LEN=299 
Feb 19 17:43:43 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094623.0955] manager: sleep requested (sleeping: no  enabled: yes)
Feb 19 17:43:43 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094623.0959] manager: sleeping...
Feb 19 17:43:43 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094623.0960] manager: NetworkManager state is now ASLEEP
Feb 19 17:43:43 LillyDell-T1600 systemd[1]: Reached target Sleep.
Feb 19 17:43:43 LillyDell-T1600 systemd[1]: Starting Suspend...
Feb 19 17:43:43 LillyDell-T1600 systemd-sleep[8971]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
Feb 19 17:43:43 LillyDell-T1600 systemd-sleep[8972]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
Feb 19 17:43:43 LillyDell-T1600 systemd-sleep[8971]: Suspending system...
Feb 19 17:43:43 LillyDell-T1600 kernel: [ 3578.074278] PM: Syncing filesystems ... done.
Feb 19 17:43:43 LillyDell-T1600 kernel: [ 3578.106739] PM: Preparing system for sleep (mem)
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.696595] Freezing user space processes ... (elapsed 0.001 seconds) done.
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.698319] OOM killer disabled.
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.698320] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.699517] PM: Suspending system (mem)
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.699537] Suspending console(s) (use no_console_suspend to debug)
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.699983] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.700086] sd 2:0:0:0: [sdb] Stopping disk
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.700120] sd 1:0:0:0: [sda] Synchronizing SCSI cache
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.700169] sd 1:0:0:0: [sda] Stopping disk
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.737780] serial 00:04: disabled
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3578.739338] e1000e: EEE TX LPI TIMER: 00000011
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.126728] PM: suspend of devices complete after 427.038 msecs
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.127308] PM: late suspend of devices complete after 0.575 msecs
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.164485] PM: noirq suspend of devices complete after 37.172 msecs
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.165031] ACPI: Preparing to enter system sleep state S3
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.165450] PM: Saving platform NVS memory
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.165474] Disabling non-boot CPUs ...
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.182058] smpboot: CPU 1 is now offline
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.206504] smpboot: CPU 2 is now offline
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.229982] smpboot: CPU 3 is now offline
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.252899] IRQ 16: no longer affine to CPU4
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.253915] smpboot: CPU 4 is now offline
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.276855] IRQ 18: no longer affine to CPU5
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.276859] IRQ 28: no longer affine to CPU5
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.277864] smpboot: CPU 5 is now offline
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.300850] IRQ 25: no longer affine to CPU6
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.301857] smpboot: CPU 6 is now offline
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.324825] IRQ 1: no longer affine to CPU7
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.324829] IRQ 9: no longer affine to CPU7
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.324836] IRQ 17: no longer affine to CPU7
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.325847] smpboot: CPU 7 is now offline
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.327454] ACPI: Low-level resume complete
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.327495] PM: Restoring platform NVS memory
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.327782] Suspended for 3.641 seconds
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.327825] Enabling non-boot CPUs ...
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.327868] x86: Booting SMP configuration:
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.327868] smpboot: Booting Node 0 Processor 1 APIC 0x2
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.330562]  cache: parent cpu1 should not be sleeping
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.330791] CPU1 is up
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.330830] smpboot: Booting Node 0 Processor 2 APIC 0x4
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.333598]  cache: parent cpu2 should not be sleeping
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.333848] CPU2 is up
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.333884] smpboot: Booting Node 0 Processor 3 APIC 0x6
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.336651]  cache: parent cpu3 should not be sleeping
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.336914] CPU3 is up
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.336948] smpboot: Booting Node 0 Processor 4 APIC 0x1
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.339802]  cache: parent cpu4 should not be sleeping
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.340088] CPU4 is up
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.340131] smpboot: Booting Node 0 Processor 5 APIC 0x3
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.343098]  cache: parent cpu5 should not be sleeping
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.343414] CPU5 is up
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.343448] smpboot: Booting Node 0 Processor 6 APIC 0x5
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.346236]  cache: parent cpu6 should not be sleeping
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.346584] CPU6 is up
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.346618] smpboot: Booting Node 0 Processor 7 APIC 0x7
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.349375]  cache: parent cpu7 should not be sleeping
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.350001] CPU7 is up
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.356397] ACPI: Waking up from system sleep state S3
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.394239] PM: noirq resume of devices complete after 37.546 msecs
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.394543] PM: early resume of devices complete after 0.282 msecs
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.395365] sd 1:0:0:0: [sda] Starting disk
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.395367] sd 2:0:0:0: [sdb] Starting disk
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.432055] serial 00:04: activated
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.732324] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.732423] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.740956] ata3.00: configured for UDMA/100
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.962224] firewire_core 0000:06:0c.0: rediscovered device fw0
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.962241] firewire_core 0000:06:0c.0: phy config: new root=ffc2, gap_count=7
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.996123] usb usb4: root hub lost power or was reset
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.996135] usb usb5: root hub lost power or was reset
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3579.996154] usb usb3: root hub lost power or was reset
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3580.342201] usb 3-4: reset high-speed USB device number 3 using ehci-pci
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3580.610188] usb 3-3: reset high-speed USB device number 2 using ehci-pci
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3580.838201] usb 3-4.3: reset full-speed USB device number 6 using ehci-pci
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3581.214179] usb 3-4.2: reset low-speed USB device number 5 using ehci-pci
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3581.590173] usb 3-3.2: reset full-speed USB device number 4 using ehci-pci
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3581.778161] usb 3-3.3: reset high-speed USB device number 7 using ehci-pci
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.010184] PM: resume of devices complete after 2615.667 msecs
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.511394] ata1.00: configured for UDMA/133
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.511874] PM: Finishing wakeup.
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.511875] OOM killer enabled.
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.511876] Restarting tasks ... 
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.513096] pci_bus 0000:02: Allocating resources
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.513118] pci_bus 0000:03: Allocating resources
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.513244] pci_bus 0000:01: Allocating resources
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.513471] pci_bus 0000:05: Allocating resources
Feb 19 17:43:51 LillyDell-T1600 systemd[1]: Time has been changed
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.515690] done.
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.1857] device (eno1): link disconnected (deferring action for 4 seconds)
Feb 19 17:43:51 LillyDell-T1600 systemd-sleep[8971]: System resumed.
Feb 19 17:43:51 LillyDell-T1600 systemd[1708]: Time has been changed
Feb 19 17:43:51 LillyDell-T1600 systemd-sleep[8971]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.2781] device (eno1): link connected
Feb 19 17:43:51 LillyDell-T1600 kernel: [ 3582.605465] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.2782] device (eno1): DHCPv4 lease renewal requested
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.3423] dhcp4 (eno1): canceled DHCP transaction, DHCP client pid 8203
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.3424] dhcp4 (eno1): state changed bound -> done
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.3429] dhcp4 (eno1): activation: beginning transaction (timeout in 45 seconds)
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.3443] dhcp4 (eno1): dhclient started with pid 9127
Feb 19 17:43:51 LillyDell-T1600 dhclient[9127]: DHCPREQUEST of 10.0.1.64 on eno1 to 255.255.255.255 port 67 (xid=0x54234c8)
Feb 19 17:43:51 LillyDell-T1600 dhclient[9127]: DHCPACK of 10.0.1.64 from 10.0.1.1
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.4330]   address 10.0.1.64
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.4331]   plen 24 (255.255.255.0)
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.4331]   gateway 10.0.1.1
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.4331]   server identifier 10.0.1.1
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.4331]   lease time 86400
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.4331]   nameserver '10.0.1.1'
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.4331]   domain name 'gci.net'
Feb 19 17:43:51 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094631.4331] dhcp4 (eno1): state changed unknown -> bound
Feb 19 17:43:51 LillyDell-T1600 dbus[989]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb 19 17:43:51 LillyDell-T1600 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb 19 17:43:51 LillyDell-T1600 dhclient[9127]: bound to 10.0.1.64 -- renewal in 42391 seconds.
Feb 19 17:43:51 LillyDell-T1600 dbus[989]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 19 17:43:51 LillyDell-T1600 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb 19 17:43:51 LillyDell-T1600 nm-dispatcher: req:1 'dhcp4-change' [eno1]: new request (1 scripts)
Feb 19 17:43:51 LillyDell-T1600 nm-dispatcher: req:1 'dhcp4-change' [eno1]: start running ordered scripts...
Feb 19 17:43:51 LillyDell-T1600 acpid: client 1301[0:0] has disconnected
Feb 19 17:43:51 LillyDell-T1600 acpid: client connected from 1301[0:0]
Feb 19 17:43:51 LillyDell-T1600 acpid: 1 client rule loaded
Feb 19 17:43:53 LillyDell-T1600 kernel: [ 3584.782129] ata2: link is slow to respond, please be patient (ready=0)
Feb 19 17:43:57 LillyDell-T1600 kernel: [ 3588.562094] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Feb 19 17:43:57 LillyDell-T1600 kernel: [ 3588.572513] ata2.00: configured for UDMA/133
Feb 19 17:43:57 LillyDell-T1600 systemd-sleep[9103]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
Feb 19 17:43:57 LillyDell-T1600 systemd[1]: Started Suspend.
Feb 19 17:43:57 LillyDell-T1600 systemd[1]: sleep.target: Unit not needed anymore. Stopping.
Feb 19 17:43:57 LillyDell-T1600 systemd[1]: Stopped target Sleep.
Feb 19 17:43:57 LillyDell-T1600 systemd[1]: Reached target Suspend.
Feb 19 17:43:57 LillyDell-T1600 systemd[1]: suspend.target: Unit is bound to inactive unit systemd-suspend.service. Stopping, too.
Feb 19 17:43:57 LillyDell-T1600 systemd[1]: Stopped target Suspend.
Feb 19 17:43:57 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094637.3213] manager: wake requested (sleeping: yes  enabled: yes)
Feb 19 17:43:57 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094637.3214] manager: waking up...
Feb 19 17:43:57 LillyDell-T1600 systemd[1]: Started Run anacron jobs at resume.
Feb 19 17:43:57 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094637.3215] device (eno1): state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Feb 19 17:43:57 LillyDell-T1600 systemd[1]: Started Run anacron jobs.
Feb 19 17:43:57 LillyDell-T1600 anacron[9202]: Anacron 2.3 started on 2018-02-19
Feb 19 17:43:57 LillyDell-T1600 anacron[9202]: Normal exit (0 jobs run)
Feb 19 17:43:57 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094637.3537] dhcp4 (eno1): canceled DHCP transaction, DHCP client pid 9127
Feb 19 17:43:57 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094637.3537] dhcp4 (eno1): state changed bound -> done
Feb 19 17:43:57 LillyDell-T1600 avahi-daemon[1014]: Withdrawing address record for 10.0.1.64 on eno1.
Feb 19 17:43:57 LillyDell-T1600 avahi-daemon[1014]: Leaving mDNS multicast group on interface eno1.IPv4 with address 10.0.1.64.
Feb 19 17:43:57 LillyDell-T1600 avahi-daemon[1014]: Interface eno1.IPv4 no longer relevant for mDNS.
Feb 19 17:43:57 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094637.3551] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb 19 17:43:57 LillyDell-T1600 dnsmasq[8193]: setting upstream servers from DBus
Feb 19 17:43:57 LillyDell-T1600 avahi-daemon[1014]: Withdrawing address record for fe80::1054:6906:b7bd:f9e9 on eno1.
Feb 19 17:43:57 LillyDell-T1600 avahi-daemon[1014]: Leaving mDNS multicast group on interface eno1.IPv6 with address fe80::1054:6906:b7bd:f9e9.
Feb 19 17:43:57 LillyDell-T1600 avahi-daemon[1014]: Interface eno1.IPv6 no longer relevant for mDNS.
Feb 19 17:43:57 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094637.3866] manager: NetworkManager state is now CONNECTED_LOCAL
Feb 19 17:43:57 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094637.4857] manager: NetworkManager state is now DISCONNECTED
Feb 19 17:43:57 LillyDell-T1600 kernel: [ 3588.812873] e1000e: eno1 NIC Link is Down
Feb 19 17:43:57 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094637.4898] device (eno1): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 19 17:43:57 LillyDell-T1600 kernel: [ 3588.817812] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
Feb 19 17:43:57 LillyDell-T1600 nm-dispatcher: req:2 'down' [eno1]: new request (1 scripts)
Feb 19 17:43:57 LillyDell-T1600 nm-dispatcher: req:2 'down' [eno1]: start running ordered scripts...
Feb 19 17:43:57 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094637.7069] device (eno1): link disconnected
Feb 19 17:43:57 LillyDell-T1600 kernel: [ 3589.034431] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
Feb 19 17:43:58 LillyDell-T1600 cinnamon-screensaver-pam-helper: pam_ecryptfs: seteuid error
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: Deleting interface #16 eno1, 10.0.1.64#123, interface stats: received=301, sent=309, dropped=0, active_time=1120 secs
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 69.164.198.192 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 216.6.2.70 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 50.116.38.157 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 108.59.2.24 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 173.230.144.109 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 216.229.4.66 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 162.210.111.4 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 4.53.160.75 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 208.88.126.235 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 129.6.15.30 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 199.188.48.60 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 96.244.96.19 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 199.101.100.221 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 208.75.88.4 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 173.230.235.13 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: 162.248.241.94 local addr 10.0.1.64 -> <null>
Feb 19 17:43:59 LillyDell-T1600 ntpd[1109]: Deleting interface #18 eno1, fe80::1054:6906:b7bd:f9e9%2#123, interface stats: received=0, sent=0, dropped=0, active_time=1118 secs
Feb 19 17:43:59 LillyDell-T1600 ModemManager[972]: <info>  Couldn't check support for device at '/sys/devices/pci0000:00/0000:00:19.0': not supported by any plugin
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1289] device (eno1): link connected
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1294] device (eno1): state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Feb 19 17:44:01 LillyDell-T1600 kernel: [ 3592.456173] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Feb 19 17:44:01 LillyDell-T1600 kernel: [ 3592.456214] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1306] policy: auto-activating connection 'Wired connection 1'
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1318] device (eno1): Activation: starting connection 'Wired connection 1' (82d39e64-93fd-32ff-9df2-8ab3b09f7082)
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1345] device (eno1): state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1346] manager: NetworkManager state is now CONNECTING
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1353] device (eno1): state change: prepare -> config (reason 'none') [40 50 0]
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1360] device (eno1): state change: config -> ip-config (reason 'none') [50 70 0]
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1368] dhcp4 (eno1): activation: beginning transaction (timeout in 45 seconds)
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1385] dhcp4 (eno1): dhclient started with pid 9259
Feb 19 17:44:01 LillyDell-T1600 dhclient[9259]: DHCPREQUEST of 10.0.1.64 on eno1 to 255.255.255.255 port 67 (xid=0x7748c0d2)
Feb 19 17:44:01 LillyDell-T1600 dhclient[9259]: DHCPACK of 10.0.1.64 from 10.0.1.1
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1955]   address 10.0.1.64
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1955]   plen 24 (255.255.255.0)
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1956]   gateway 10.0.1.1
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1956]   server identifier 10.0.1.1
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1956]   lease time 86400
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1956]   nameserver '10.0.1.1'
Feb 19 17:44:01 LillyDell-T1600 avahi-daemon[1014]: Joining mDNS multicast group on interface eno1.IPv4 with address 10.0.1.64.
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1957]   domain name 'gci.net'
Feb 19 17:44:01 LillyDell-T1600 avahi-daemon[1014]: New relevant interface eno1.IPv4 for mDNS.
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1957] dhcp4 (eno1): state changed unknown -> bound
Feb 19 17:44:01 LillyDell-T1600 avahi-daemon[1014]: Registering new address record for 10.0.1.64 on eno1.IPv4.
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1980] device (eno1): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1991] device (eno1): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.1997] device (eno1): state change: secondaries -> activated (reason 'none') [90 100 0]
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.2004] manager: NetworkManager state is now CONNECTED_LOCAL
Feb 19 17:44:01 LillyDell-T1600 dhclient[9259]: bound to 10.0.1.64 -- renewal in 35159 seconds.
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.2070] manager: NetworkManager state is now CONNECTED_GLOBAL
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.2070] policy: set 'Wired connection 1' (eno1) as default for IPv4 routing and DNS
Feb 19 17:44:01 LillyDell-T1600 NetworkManager[8184]: <info>  [1519094641.2072] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb 19 17:44:01 LillyDell-T1600 dnsmasq[8193]: setting upstream servers from DBus
Feb 19 17:44:01 LillyDell-T1600 dnsmasq[8193]: using nameserver 10.0.1.1#53(via eno1)
Feb 19 17:44:02 LillyDell-T1600 avahi-daemon[1014]: Joining mDNS multicast group on interface eno1.IPv6 with address fe80::1054:6906:b7bd:f9e9.
Feb 19 17:44:02 LillyDell-T1600 avahi-daemon[1014]: New relevant interface eno1.IPv6 for mDNS.
Feb 19 17:44:02 LillyDell-T1600 avahi-daemon[1014]: Registering new address record for fe80::1054:6906:b7bd:f9e9 on eno1.*.
Feb 19 17:44:04 LillyDell-T1600 ntpd[1109]: Listen normally on 19 eno1 10.0.1.64:123
Feb 19 17:44:04 LillyDell-T1600 ntpd[1109]: Listen normally on 20 eno1 [fe80::1054:6906:b7bd:f9e9%2]:123
Feb 19 17:44:04 LillyDell-T1600 ntpd[1109]: new interface(s) found: waking up resolver
Feb 19 17:44:04 LillyDell-T1600 kernel: [ 3595.820217] [UFW BLOCK] IN=eno1 OUT= MAC=5c:f9:dd:70:14:07:54:88:0e:b3:d2:b4:08:00 SRC=10.0.1.52 DST=10.0.1.64 LEN=359 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38648 DPT=50920 LEN=339 
Feb 19 17:44:04 LillyDell-T1600 kernel: [ 3595.820811] [UFW BLOCK] IN=eno1 OUT= MAC=5c:f9:dd:70:14:07:90:f1:aa:f1:bb:a6:08:00 SRC=10.0.1.57 DST=10.0.1.64 LEN=319 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=50920 LEN=299
I cannot figure out why this machine won't stay suspended.  :?

```

I can't glean anything from those logs that would be causing this machine to be immediately resuming from suspend.  Maybe someone with a keener eye and way more expertise can help me out?

Things I've tried:

[LIST]
[*]Updating the BIOS
[*]Ensuring wake on lan is disabled in BIOS
[*]Disabling my network adapter altogeather
[*]Updating the kernel
[*]Making sure my 3rd party drivers are good
[*]Disabling acpi USB ports that were enabled in acordance with [this thread]("https://askubuntu.com/questions/148481/how-do-i-prevent-immediate-wake-up-from-suspend-and-or-hibernation").
[/LIST]

I am truly at a loss.  Any help or suggestions would be greatly appreciated.

---

### Post by #&amp;thj^% on 2018-02-25
How big is your swap?
To see 
```
free
```
And going to some older files I kept with my short time with Mint I found this to be useful for my setup any way. :)
```
gsettings set org.cinnamon.desktop.session screensaver-uses-logind false
```

---

### Post by bug67 on 2018-02-25
"free" returns:
```
total        used        free      shared  buff/cache   available
Mem:       16380504      628808    14978088       48316      773608    15355440
Swap:      16733180           0    16733180

```

And, I'm assuming that second command will disable the need for logging in when returning from the screensaver?  And if I want to go back, I just change it to "...logind true?"

---

### Post by #&amp;thj^% on 2018-02-26
> **bug67 said:**
> 
And, I'm assuming that second command will disable the need for logging in when returning from the screensaver?  And if I want to go back, I just change it to "...logind true?"

Yes that's correct.

---

### Post by bug67 on 2018-02-27
> **1fallen said:**
> 
```
gsettings set org.cinnamon.desktop.session screensaver-uses-logind false
```

I got:

```
No such key 'screensaver-uses-logind'
```

Doesn't matter. I switched the "Lock the computer when the screensaver starts" off via the GUI.  Had no effect.  Computer still immediately woke from suspend.

Another thing I thought I might try was to boot from the install media and invoke suspend from there.  Same thing.  Immediate resume.  Me thinks it's a hardware issue.  :(

---

