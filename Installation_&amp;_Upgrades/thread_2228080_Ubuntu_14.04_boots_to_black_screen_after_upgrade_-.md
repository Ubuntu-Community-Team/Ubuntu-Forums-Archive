---
title: "Ubuntu 14.04 boots to black screen after upgrade - problem seems to be X connected"
date: 2014-06-05
forum: Installation &amp; Upgrades
---

### Post by Alice_Gabriel on 2014-06-05
Hi,

I just spent a day trying to work around my newly upgraded Ubuntu 14.04 booting into a black screen without success and becoming desparated. 


What I did: Upgrade to 14.04 LTS from 13.10 via command line. Everything procceeded without problems.

The status now: GRUB shows. After I select any Ubuntu starting option I still have on my system, the Ubuntu start screen with the dots appears, changes into a black screen with a white cursor in the upper front corner. At this stage nothing will get me out of this besides a manual restart (Alt + F1 or F2 does not work, no keyboard reactions otherwise). This effect also happens with the Ubuntu 13.10 kernel stilled imaged on the system. Graphics failsafe modes won't boot at all.

My system: 
[http://paste.ubuntu.com/7596717/](http://paste.ubuntu.com/7596717/)

Thinkpad X1, dualboot with Windows 7. Intel HD 4000 graphics card. 
There is no file /etc/X11/xorg/conf.

 lspci -nnk | grep -iA3 vga gives:

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Lenovo Device [17aa:21f9]
    Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)

/usr/lib/nux/unity_support_test -p gives:

No protocol specified
Error: unable to open display

What I tried:
Many suggested solutions from other forum threads, including 
Resetting unity, dpkg --reconfigure, several uninstallation and reinstallation of fglrx / nouveau / nvidia graphics drivers

Booting 14.04 from a life USB, which works great and enables me to write this post, but I don't manage to fix my local 14.04 installation :(

Any ideas? 

Thanks a lot,
Alice

---

### Post by Alice_Gabriel on 2014-06-06
I decided to fresh install 14.04 from a life USB following this: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation).
In the test system and in 13.10 usb and all my networks were working  out of the box (bluetooth, ethernet, wifi, GSM card). 
First thing ater installation I ran into a  login-loop problem, due to wrong permissions of the .Xauthority file (see [http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)).  Now I have no network adapters and no USB ports at all being recognized.
ifconfig yields:
  lo    Link encap:Local Loopback  
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:65536  Metric:1
      RX packets:293 errors:0 dropped:0 overruns:0 frame:0
      TX packets:293 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0 
      RX bytes:21825 (21.8 KB)  TX bytes:21825 (21.8 KB)
  iwconfig yields:
  lo        no wireless extensions.
  sudo lshw -C network gives:
   *-network UNCLAIMED     
   description: Network controller
   product: Centrino Advanced-N 6205 [Taylor Peak]
   vendor: Intel Corporation
   physical id: 0
   bus info: pci@0000:03:00.0
   version: 96
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list
   configuration: latency=0
   resources: memory:f0c00000-f0c01fff
  In my dual boot Windows 7 all network is working fine.
  Could that all be a simple problem with some network config file?

---

