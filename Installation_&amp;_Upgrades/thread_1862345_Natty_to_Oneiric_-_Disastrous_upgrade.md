---
title: "Natty to Oneiric - Disastrous upgrade"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by iFreeBudget on 2011-10-16
I had a pretty stable Natty install, but then I went and upgraded to 11.10. It went downhill from there. Most of my problems I am about to describe are covered in various threads but none of the solutions have worked for me. 

I have a Asus laptop model no: U56E-BBL5 with 6gb RAM, Intel core i5

1. Wireless/wifi stopped working. Outputs from various commands suggested in other threads are pasted here

```
me@me-ubuntu:~$ rfkill list
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wimax: WiMAX
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

me@me-ubuntu:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

me@me-ubuntu:~$ dmesg | grep -i firm
[    0.811564] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   15.539802] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   15.667238] elantech: assuming hardware version 3, firmware version 69.15.1

me@me-ubuntu:~$ lspci | grep -i network
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)

me@me-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

me@me-ubuntu:~$ sudo lshw -C network
[sudo] password for me: 
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:34:fe:d4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:50 memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 14:da:e9:2a:1e:bc
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:53 memory:dd400000-dd43ffff ioport:a000(size=128)

```So, wireless is completely not working now and I have to sit near by shoe closet on the floor to get a wired connection to post this.:(

2. Suspend hangs the system.

Whenever I suspend or system goes to suspend due to inactivity, the system completely freezes. Only a hard reset is possible at this time. 

3. System is generally slow and unreliable. Only saving grace has been Gnome3.2 which looks rather neat.

Any help is greatly appreciated and any one else having same problems please give a shout. I would feel a little better knowing that I am not alone having these problems.

---

### Post by carljmoss on 2011-10-19
> **iFreeBudget said:**
> I would feel a little better knowing that I am not alone having these problems.

There's some consolation in shared misery. I upgraded my eeePC from Kubuntu Natty to Oneiric and now ifconfig doesn't even show wlan0. I can toggle the blue light on the front panel off and on, but it makes no difference. I even tried installing the Debian firmware-ralink package, but with no joy.

---

### Post by ezroot on 2011-10-20
Same problem here with exactly the same laptop model: Asus U56E

Everything seems to be working fine except for wifi and suspend.
Wireless card appears to connect to the AP but would time out after about 30 seconds.

I found a workaround on the suspend problem.
Follow "Step 2" (not "Step 2 old") here -> [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")

I hope the wireless problem gets resolved soon.

---

### Post by davegunnoe on 2011-10-24
Hey folks.

Same laptop here. It's not a nice fix, but go back to the previous kernel. I believe the issue is with Linux Kernel 3. Good luck.

---

### Post by sammiev on 2011-10-24
It seems most people with these problems sooner or later do a fresh install. :)

---

### Post by MonocleMike2 on 2011-10-25
That's what I did on one laptop - an old Toshiba Satellite Pro.  In Windows I uninstalled Ubuntu and re-formatted the partition and did a clean install of 11.04 from the web.  The attempts to use a USB stick having previously failed.  I can't/don't use Unity GUI on this one.
The other laptop - a slightly younger MiNote - upgraded to 11.10 without problem and I use that regularly though subjectively I think the old one is faster.  I suspect that is the difference between the GUIs.

---

