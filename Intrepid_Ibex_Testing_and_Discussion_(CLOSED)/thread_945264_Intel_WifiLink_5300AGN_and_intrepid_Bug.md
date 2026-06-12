---
title: "Intel WifiLink 5300AGN and intrepid: Bug?"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Fischli on 2008-10-12
Hi everybody

I was testing a Lenovo X200 with a Intel WifiLink 5300AGN with the daily Live-CD image (11.10.2008 ) of Intrepid. The card was recognized during boot and the driver/firmware was loaded but then an error occurred (see dmesg output below).

After that the card interface wlan0 was available, the wifi-led on the notebook was on but iwlist wlan0 scan did not return any results and ifconfig wlan0 up produced another error in the dmesg output.

I also did a 
```
sudo rmmod iwlang && sudo modprobe iwlagn
```
which resulted in the same output in dmesg as after boot.

I tested this both with the 32 and 64 bit versions, same result.

Did anybody get the card working properly? Or could this be a potential bug and should be reported?

dmesg after booting:

```
[ 250.503252] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[ 250.503258] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[ 250.503341] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 250.503380] iwlagn 0000:03:00.0: setting latency timer to 64
[ 250.503429] iwlagn: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[ 250.532152] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 250.541246] phy1: Selected rate control algorithm 'iwl-agn-rs'
[ 254.573157] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 254.575501] firmware: requesting iwlwifi-5000-1.ucode
[ 256.739716] Registered led device: iwl-phy1:radio
[ 256.740319] Registered led device: iwl-phy1:assoc
[ 256.740798] Registered led device: iwl-phy1:RX
[ 256.741262] Registered led device: iwl-phy1:TX
[ 257.240272] iwlagn: Error sending REPLY_ADD_STA: time out after 500ms.
```

iwlist:

```
ubuntu@ubuntu:~$ iwlist wlan0 scan
wlan0 No scan results 
```

ifconfig down/up, dmesg output:

```
[ 645.720676] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 645.750874] Registered led device: iwl-phy1:radio
[ 645.751440] Registered led device: iwl-phy1:assoc
[ 645.751907] Registered led device: iwl-phy1:RX
[ 645.752360] Registered led device: iwl-phy1:TX
[ 645.769197] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

lspci -v

```
03:00.0 Network controller: Intel Corporation Device 4236
Subsystem: Intel Corporation Device 1011
Flags: bus master, fast devsel, latency 0, IRQ 218
Memory at f2500000 (64-bit, non-prefetchable) [size=8K]
Capabilities: [c8] Power Management version 3
Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
Capabilities: [e0] Express Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting <?>
Capabilities: [140] Device Serial Number XX-XX-XX-XX-XX-XX-XX-XX
Kernel driver in use: iwlagn
Kernel modules: iwlagn
```

lshw -C network

```
*-network               

      description: Ethernet interface

      product: 82567LM Gigabit Network Connection

      vendor: Intel Corporation

      physical id: 19

      bus info: pci@0000:00:19.0

      logical name: eth0

      version: 03

      serial: XX:XX:XX:XX:XX:XX

      size: 10MB/s

      capacity: 1GB/s

      width: 32 bits

      clock: 33MHz


      capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation

      configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=half firmware=1.8-3 ip=192.168.1.15 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=10MB/s

 *-network

      description: Wireless interface

      product: Intel Corporation

      vendor: Intel Corporation

      physical id: 0

      bus info: pci@0000:03:00.0

      logical name: wmaster0

      version: 00

      serial: XX:XX:XX:XX:XX:XX

      width: 64 bits

      clock: 33MHz

      capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless

      configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

 *-network DISABLED

      description: Ethernet interface

      physical id: 2

      logical name: pan0


      serial: XX:XX:XX:XX:XX:XX

      capabilities: ethernet physical

      configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by Fischli on 2008-10-12
Sorry. Wrong place to post, see
   [http://ubuntuforums.org/showthread.php?t=945270](http://ubuntuforums.org/showthread.php?t=945270)

---

