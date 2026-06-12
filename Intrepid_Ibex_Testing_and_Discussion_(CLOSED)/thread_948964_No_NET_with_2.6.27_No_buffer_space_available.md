---
title: "No NET with 2.6.27: No buffer space available"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by grigio on 2008-10-15
With kernel 2.6.27-x the network doesn't work anymore, last working kernel is 2.6.26-5 :(

ubuntu@ubuntu:~$ sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0
SIOCSIFADDR: No buffer space available
SIOCSIFNETMASK: Cannot assign requested address

dmesg
```
[  225.434919] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  225.435343] ATL1E 0000:02:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  225.435811] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  229.644016] usb 1-3: device descriptor read/64, error -110
[  240.232015] usb 1-3: device descriptor read/64, error -110
[  240.448013] usb 1-3: new high speed USB device using ehci_hcd and address 7
[  246.736012] usb 1-3: device not accepting address 7, error -71
[  246.848009] usb 1-3: new high speed USB device using ehci_hcd and address 8
[  252.776011] usb 1-3: device not accepting address 8, error -71
[  252.776028] hub 1-0:1.0: unable to enumerate USB device on port 3
[  253.044010] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  265.163122] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  265.163259] ATL1E 0000:02:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  265.163363] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```

---

