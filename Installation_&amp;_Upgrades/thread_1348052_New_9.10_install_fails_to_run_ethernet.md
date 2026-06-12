---
title: "New 9.10 install fails to run ethernet"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by DavidTangye on 2009-12-06
My main PC has run Ubuntu versions 9.04, and previously 8.10. However after installing 9.10 into a new partition (which uses ethernet via a live CD image via netboot) & then rebooting, I find that the installed Ubuntu does not run the ethernet device. So I have no network. 

ifconfig lists "lo" only.

The outputs of lshw is attached, for both 9.04, and 9.10. In summary:

Both show this -
```
    description: Desktop Computer
    product: M61SME-S2
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=30303144-3744-4242-3146-3446FFFFFFFF
```Running 9.04, the ethernet device shows:
```
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1d:7d:bb:1f:4f
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.43 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
```but under 9.10 these lines differ:
```
     *-bridge DISABLED
 ...
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:20 memory:fb006000-fb006fff ioport:cc00(size=8)
```I am wondering whether the forcedeth driver version 0.64 might be a problem for my hardware? How would I find out more about this?

I have also incuded the outputs of "diff -u" for the outputs of lshw and also for "lspci -vv" for 9.04 & 9.10.

Any other ideas about how to find and fix the problem?

---

### Post by DavidTangye on 2009-12-26
No response, but never mind. I found a workaround. I installed 9.10 via the min.iso and therefore got the latest software installed immediately. On first reboot after the install, the system is working fine.

This has happened before too, ie where Ubuntu 6 monthly releases have problems which are subsequently fixed. It seems to me that the mini.iso is a valuable facility, as it avoids this sort of problem.

---

