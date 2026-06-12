---
title: "Installation not detecting Wireless Card."
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by Vry on 2012-10-06
Installed Easy Peasy, just an ubuntu derivative centered around Unity, and am having a hellish time with it not finding the wireless card:

```
 root@sonata:~# uname -a
Linux sonata 2.6.32-43-generic #97-Ubuntu SMP Wed Sep 5 16:43:09 UTC 2012 i686 GNU/Linux
``````
root@sonata:~# lshw -short
H/W path           Device      Class          Description
=========================================================
                               system         P151EMx
/0                             bus            P151EMx
/0/0                           memory         64KiB BIOS
/0/10                          memory         1MiB L2 cache
/0/11                          memory         128KiB L1 cache
/0/12                          memory         6MiB L3 cache
/0/13                          memory         16GiB System Memory
/0/13/0                        memory         4GiB SODIMM Synchronous 1600 MHz (0.6 ns)
/0/13/1                        memory         4GiB SODIMM Synchronous 1600 MHz (0.6 ns)
/0/13/2                        memory         4GiB SODIMM Synchronous 1600 MHz (0.6 ns)
/0/13/3                        memory         4GiB SODIMM Synchronous 1600 MHz (0.6 ns)
/0/14                          processor      Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
/0/14/3.1                      processor      Logical CPU
/0/14/3.2                      processor      Logical CPU
/0/14/3.3                      processor      Logical CPU
/0/14/3.4                      processor      Logical CPU
/0/14/3.5                      processor      Logical CPU
/0/14/3.6                      processor      Logical CPU
/0/14/3.7                      processor      Logical CPU
/0/14/3.8                      processor      Logical CPU
/0/14/3.9                      processor      Logical CPU
/0/14/3.a                      processor      Logical CPU
/0/14/3.b                      processor      Logical CPU
/0/14/3.c                      processor      Logical CPU
/0/14/3.d                      processor      Logical CPU
/0/14/3.e                      processor      Logical CPU
/0/14/3.f                      processor      Logical CPU
/0/14/3.10                     processor      Logical CPU
/0/1                           processor      
/0/1/3.1                       processor      Logical CPU
/0/1/3.2                       processor      Logical CPU
/0/1/3.3                       processor      Logical CPU
/0/1/3.4                       processor      Logical CPU
/0/1/3.5                       processor      Logical CPU
/0/1/3.6                       processor      Logical CPU
/0/1/3.7                       processor      Logical CPU
/0/1/3.8                       processor      Logical CPU
/0/1/3.9                       processor      Logical CPU
/0/1/3.a                       processor      Logical CPU
/0/1/3.b                       processor      Logical CPU
/0/1/3.c                       processor      Logical CPU
/0/1/3.d                       processor      Logical CPU
/0/1/3.e                       processor      Logical CPU
/0/1/3.f                       processor      Logical CPU
/0/1/3.10                      processor      Logical CPU
/0/2                           processor      
/0/2/3.1                       processor      Logical CPU
/0/2/3.2                       processor      Logical CPU
/0/2/3.3                       processor      Logical CPU
/0/2/3.4                       processor      Logical CPU
/0/2/3.5                       processor      Logical CPU
/0/2/3.6                       processor      Logical CPU
/0/2/3.7                       processor      Logical CPU
/0/2/3.8                       processor      Logical CPU
/0/2/3.9                       processor      Logical CPU
/0/2/3.a                       processor      Logical CPU
/0/2/3.b                       processor      Logical CPU
/0/2/3.c                       processor      Logical CPU
/0/2/3.d                       processor      Logical CPU
/0/2/3.e                       processor      Logical CPU
/0/2/3.f                       processor      Logical CPU
/0/2/3.10                      processor      Logical CPU
/0/3                           processor      
/0/3/3.1                       processor      Logical CPU
/0/3/3.2                       processor      Logical CPU
/0/3/3.3                       processor      Logical CPU
/0/3/3.4                       processor      Logical CPU
/0/3/3.5                       processor      Logical CPU
/0/3/3.6                       processor      Logical CPU
/0/3/3.7                       processor      Logical CPU
/0/3/3.8                       processor      Logical CPU
/0/3/3.9                       processor      Logical CPU
/0/3/3.a                       processor      Logical CPU
/0/3/3.b                       processor      Logical CPU
/0/3/3.c                       processor      Logical CPU
/0/3/3.d                       processor      Logical CPU
/0/3/3.e                       processor      Logical CPU
/0/3/3.f                       processor      Logical CPU
/0/3/3.10                      processor      Logical CPU
/0/100                         bridge         Intel Corporation
/0/100/1                       bridge         Intel Corporation
/0/100/1/0                     display        nVidia Corporation
/0/100/2                       display        Intel Corporation
/0/100/14                      bus            Intel Corporation
/0/100/16                      communication  Intel Corporation
/0/100/1a                      bus            Intel Corporation
/0/100/1b                      multimedia     Intel Corporation
/0/100/1c                      bridge         Intel Corporation
/0/100/1c.1                    bridge         Intel Corporation
/0/100/1c.1/0                  generic        Realtek Semiconductor Co., Ltd.
/0/100/1c.1/0.2    eth0        network        RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1c.2                    bridge         Intel Corporation
/0/100/1c.2/0                  network        Realtek Semiconductor Co., Ltd.
/0/100/1c.3                    bridge         Intel Corporation
/0/100/1c.3/0                  bus            IEEE 1394 Host Controller
/0/100/1d                      bus            Intel Corporation
/0/100/1f                      bridge         Intel Corporation
/0/100/1f.2        scsi1       storage        Intel Corporation
/0/100/1f.2/0      /dev/sda    disk           120GB INTEL SSDSC2CW12
/0/100/1f.2/0/1    /dev/sda1   volume         100MiB Windows NTFS volume
/0/100/1f.2/0/2    /dev/sda2   volume         58GiB Windows NTFS volume
/0/100/1f.2/0/3    /dev/sda3   volume         39GiB Windows NTFS volume
/0/100/1f.2/0/4    /dev/sda4   volume         14GiB Extended partition
/0/100/1f.2/0/4/5  /dev/sda5   volume         121MiB Linux filesystem partition
/0/100/1f.2/0/4/6  /dev/sda6   volume         976MiB Linux filesystem partition
/0/100/1f.2/0/4/7  /dev/sda7   volume         976MiB Linux filesystem partition
/0/100/1f.2/0/4/8  /dev/sda8   volume         7152MiB Linux filesystem partition
/0/100/1f.2/0/4/9  /dev/sda9   volume         976MiB Linux swap / Solaris partition
/0/100/1f.2/0/4/a  /dev/sda10  volume         4265MiB Linux filesystem partition
/0/100/1f.2/1      /dev/cdrom  disk           BD-CMB UJ141AF
/0/100/1f.3                    bus            Intel Corporation
/1                             power          To Be Filled By O.E.M.

``````
root@sonata:~# lspci
00:00.0 Host bridge: Intel Corporation Device 0154 (rev 09)
00:01.0 PCI bridge: Intel Corporation Device 0151 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0166 (rev 09)
00:14.0 USB Controller: Intel Corporation Device 1e31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 1e3a (rev 04)
00:1a.0 USB Controller: Intel Corporation Device 1e2d (rev 04)
00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 1e10 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Device 1e12 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Device 1e14 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Device 1e16 (rev c4)
00:1d.0 USB Controller: Intel Corporation Device 1e26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1e57 (rev 04)
00:1f.2 SATA controller: Intel Corporation Device 1e03 (rev 04)
00:1f.3 SMBus: Intel Corporation Device 1e22 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 1213 (rev a1)
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
``````
root@sonata:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
``````
root@sonata:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:90:f5:d0:ec:9b  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fed0:ec9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118783756 (118.7 MB)  TX bytes:4073513 (4.0 MB)
          Interrupt:30 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8048 (8.0 KB)  TX bytes:8048 (8.0 KB)

pan0      Link encap:Ethernet  HWaddr ce:46:20:70:48:1e  
          inet6 addr: fe80::cc46:20ff:fe70:481e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

```Just in case...
```
root@sonata:~# lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 5986:0361 Acer, Inc 
Bus 002 Device 004: ID 147e:1002 Upek 
Bus 002 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```Don't have a hardware switch, although there is a software switch as far are the keyboard bits go, and a corresponding light that says whether it thinks wireless is enabled or disabled.  More than happy to give any other information - I have zero experience with Ubuntu, though I have a fair bit of experience with other distributions.  Wireless works in Windows flawlessly, obviously just having issues with it existing here in Linux.

---

### Post by Vry on 2012-10-06
Booted into Windows:

```
Realtek RTL8723AE Wireless LAN 802.11N PCI-E NIC
C:\Windows\System32\DRIVERS\rtwlane.sys
C:\Windows\system32\drivers\vwfibus.sy
PCI bus , device , function 0
oem19.inf
inf section: RTL872ae.ndi
```

Perusing forum posts and looks like there exists an rtlwifi package that isn't in the standard repos that may have the drivers.  Still would take any help I can get :]

---

### Post by Vry on 2012-10-06
I tried to install using the Anonymous dropbox file from May that I found a few other people had success with and hit compile errors:

```
base.c:1394: warning: 'enum ieee80211_smps_mode' declared inside parameter list
base.c:1394: error: parameter 3 ('smps') has incomplete type
base.c:1422: error: type of formal parameter 2 is incomplete
```

Was following directions found under the answer here:

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

Edit: It's late, I didn't realize just how old the kernel version I was on, was.  While it should work per the readme, I'm downloading ubuntu normal live cd and giving that a whirl.  I thought I'd read a while back that unity was discontinued in normal ubuntu, but if I can get the wireless working I imagine she'd live and learn a new DE.

---

