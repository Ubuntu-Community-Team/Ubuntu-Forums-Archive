---
title: "Bluetooth not working in 13.10 64-bit"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by gore-amit on 2014-01-03
I have installed Ubuntu 13.10 64-bit on Acer E1-530 laptop.
After ethernet not working, this is second things i have discovered.
Bluetooth does neither detect or gets discovered from any hardware :(

-Aspire-E1-530:~$ dmesg | grep Bluetooth
[   10.754836] Bluetooth: Core ver 2.16
[   10.754862] Bluetooth: HCI device and connection manager initialized
[   10.754870] Bluetooth: HCI socket layer initialized
[   10.754872] Bluetooth: L2CAP socket layer initialized
[   10.754877] Bluetooth: SCO socket layer initialized
[   15.693465] Bluetooth: RFCOMM TTY layer initialized
[   15.693478] Bluetooth: RFCOMM socket layer initialized
[   15.693480] Bluetooth: RFCOMM ver 1.11
[   15.924230] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.924234] Bluetooth: BNEP filters: protocol multicast
[   15.924280] Bluetooth: BNEP socket layer initialized

None of my 3 phones are detecting it.

-Aspire-E1-530:~$ hciconfig --all 
hci0:    Type: BR/EDR  Bus: USB
    BD Address: A4:DB:30:7D:3E:F7  ACL MTU: 1022:8  SCO MTU: 183:5
    UP RUNNING PSCAN ISCAN 
    RX bytes:1781 acl:0 sco:0 events:179 errors:0
    TX bytes:2907 acl:0 sco:0 commands:158 errors:0
    Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x8f
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'ubuntu-0'
    Class: 0x6e0100
    Service Classes: Networking, Rendering, Capturing, Audio, Telephony
    Device Class: Computer, Uncategorized
    HCI Version:  (0x7)  Revision: 0x3101
    LMP Version:  (0x7)  Subversion: 0x1
    Manufacturer: Atheros Communications, Inc. (69)

Applet shows Bluetooth "on" and visibility set to "on" but neither finding or pairing

---

### Post by varunendra on 2014-01-05
Try installing "blueman" package which is a relatively more capable GUI bluetooth manager than the default one. The default one sometimes shows up as "On" even though it is physically not.

If blueman doesn't help, please post the outputs of -
```
lsusb
usb-devices
```

While posting the outputs, please use 'Code' tags. It preserves the formatting of the outputs and makes them more readable. Please follow the "Using Code Tags" link in my signature to see how.

---

### Post by gore-amit on 2014-01-08
```

-Aspire-E1-530:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b3f6 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 04ca:300b Lite-On Technology Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by gore-amit on 2014-01-08
attaching output of command.

---

### Post by varunendra on 2014-01-08
Okay, the device is recognized and the driver is loaded.

Now as a guess shot, please try -
```
echo -n "0000:00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind
echo -n "0000:00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/bind
```
Keep a gap of about 4-6 seconds between the above two commands. If you get an error, like "No such file or directory", or if the trick doesn't work, post back the outputs of -
```
lspci | grep -i usb
ls -l /sys/bus/pci/drivers/e*/
```

---

### Post by gore-amit on 2014-01-10
I got "tee: /sys/bus/pci/drivers/ehci_hcd/unbind: No such file or directory" error message

```


-Aspire-E1-530:~$ lspci | grep -i usb
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
-Aspire-E1-530:~$ ls -l /sys/bus/pci/drivers/e*/
total 0
lrwxrwxrwx 1 root root    0 Jan 10 05:17 0000:00:1a.0 -> ../../../../devices/pci0000:00/0000:00:1a.0
lrwxrwxrwx 1 root root    0 Jan 10 05:17 0000:00:1d.0 -> ../../../../devices/pci0000:00/0000:00:1d.0
--w------- 1 root root 4096 Jan 10 05:17 bind
--w------- 1 root root 4096 Jan 10 05:17 new_id
--w------- 1 root root 4096 Jan 10 05:17 remove_id
--w------- 1 root root 4096 Jan 10 05:17 uevent
--w------- 1 root root 4096 Jan 10 05:17 unbind



```

---

### Post by varunendra on 2014-01-10
> **gore-amit said:**
> ```
-Aspire-E1-530:~$ **[COLOR="#800000"]ls -l /sys/bus/pci/drivers/e*/[/COLOR]**
total 0
lrwxrwxrwx 1 root root    0 Jan 10 05:17 **0000:00:1a.0** -> ../../../../devices/pci0000:00/0000:00:1a.0
lrwxrwxrwx 1 root root    0 Jan 10 05:17 0000:00:1d.0 -> ../../../../devices/pci0000:00/0000:00:1d.0
--w------- 1 root root 4096 Jan 10 05:17 bind
--w------- 1 root root 4096 Jan 10 05:17 new_id
--w------- 1 root root 4096 Jan 10 05:17 remove_id
--w------- 1 root root 4096 Jan 10 05:17 uevent
--w------- 1 root root 4096 Jan 10 05:17 **[COLOR="#FF0000"]unbind[/COLOR]**

```

So the highlighted parts tell us that the path is there, just the last folder name is not ehci_hcd, but something similar (since e* covers it). Maybe just ehci? Check with -
```
ls /sys/bus/pci/drivers
```
..and replace "**ehci_hcd**" in the unbind command with whatever name comes up starting with 'e'.

Please try the change and post back the result.

**PS:**
Just for your understanding of what we are trying here, we are detaching the particular bus (which I believe the bluetooth adapter is on) from the "ehci_hcd" driver which is a USB2 controller driver. The second (...bind) command reattaches the driver with the bus, thus simulating a 'USB reset' (or logical unplug - replug of the bluetooth device).

---

### Post by gore-amit on 2014-01-10
```

-Aspire-E1-530:~$ ls -lrt /sys/bus/pci/drivers
total 0
drwxr-xr-x 2 root root 0 Jan  8 09:58 sdhci-pci
drwxr-xr-x 2 root root 0 Jan  8 09:58 ahci
drwxr-xr-x 2 root root 0 Jan  8 09:58 tg3
drwxr-xr-x 2 root root 0 Jan  8 09:58 mei_me
drwxr-xr-x 2 root root 0 Jan  8 09:58 lpc_ich
drwxr-xr-x 2 root root 0 Jan  8 09:58 ath9k
drwxr-xr-x 2 root root 0 Jan  8 09:58 i915
drwxr-xr-x 2 root root 0 Jan  8 09:58 snd_hda_intel
drwxr-xr-x 2 root root 0 Jan  8 09:58 parport_pc
drwxr-xr-x 2 root root 0 Jan 10 05:17 ehci-pci
drwxr-xr-x 2 root root 0 Jan 10 14:55 xhci_hcd
drwxr-xr-x 2 root root 0 Jan 10 14:55 xen-platform-pci
drwxr-xr-x 2 root root 0 Jan 10 14:55 virtio-pci
drwxr-xr-x 2 root root 0 Jan 10 14:55 uhci_hcd
drwxr-xr-x 2 root root 0 Jan 10 14:55 tsi721
drwxr-xr-x 2 root root 0 Jan 10 14:55 serial
drwxr-xr-x 2 root root 0 Jan 10 14:55 pcieport
drwxr-xr-x 2 root root 0 Jan 10 14:55 pata_sis
drwxr-xr-x 2 root root 0 Jan 10 14:55 ohci-pci
drwxr-xr-x 2 root root 0 Jan 10 14:55 langwell_gpio
drwxr-xr-x 2 root root 0 Jan 10 14:55 ioapic
drwxr-xr-x 2 root root 0 Jan 10 14:55 imsttfb
drwxr-xr-x 2 root root 0 Jan 10 14:55 ata_piix
drwxr-xr-x 2 root root 0 Jan 10 14:55 ata_generic
drwxr-xr-x 2 root root 0 Jan 10 14:55 asiliantfb
drwxr-xr-x 2 root root 0 Jan 10 14:55 agpgart-via
drwxr-xr-x 2 root root 0 Jan 10 14:55 agpgart-intel

```

I replaced ehci_hcd with ehci-pci and got this:

```

-Aspire-E1-530:~$ echo -n "0000:00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/unbind
0000:00:1a.0tee: /sys/bus/pci/drivers/ehci-pci/unbind: No such device

```

---

### Post by varunendra on 2014-01-10
> **gore-amit said:**
> ```
-Aspire-E1-530:~$ echo -n "0000:00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/unbind
[COLOR="#FF0000"]0000:00:1a.0[/COLOR]
tee: /sys/bus/pci/drivers/ehci-pci/unbind: **No such device**

```

Interesting. Could you please browse to that directory (/sys/bus/pci/drivers/ehci-pci/) and see if both the items - the unbind/bind files and "[COLOR="#FF0000"]0000:00:1a.0[/COLOR]" link are there? If they are, I'm not sure why unbind says there is no such device (the message is from the unbind file, and what it says "not found" is the "[COLOR="#FF0000"]0000:00:1a.0[/COLOR]" shortcut which represents a device).

We can try a slightly different approach, but this one doesn't make sense to me.

---

### Post by gore-amit on 2014-01-10
Thanks Varun for all the help.
Just to make it clear, this laptop by default came with a linux flavor. I formatted and installed Ubuntu 13.10 on it.
Out of box neither bluetooth or ethernet is working. Isit to do with the kernel ? Currently it is 3.11.0-15-generic.

Now to answer your question.
Yes there are all two files and a link are available under the /sys/bus/pci/drivers/ehci-pci/ directory

```

-Aspire-E1-530:~$ ls -lrt /sys/bus/pci/drivers/ehci-pci/
total 0
--w------- 1 root root 4096 Jan 10 05:17 uevent
--w------- 1 root root 4096 Jan 10 05:17 remove_id
--w------- 1 root root 4096 Jan 10 05:17 new_id
--w------- 1 root root 4096 Jan 10 05:17 bind
lrwxrwxrwx 1 root root    0 Jan 10 05:17 0000:00:1d.0 -> ../../../../devices/pci0000:00/0000:00:1d.0
--w------- 1 root root 4096 Jan 10 15:00 unbind

```

---

### Post by varunendra on 2014-01-13
Sorry for not being able to reply sooner, it's getting hard to get enough time to focus on issues that don't have an obvious fix..

Anyway, could you please take a look at system logs (dmesg, kern.log, syslog in /var/log directory) yourself to see if there is some hint or something suspicious about bluetooth? If unsure, please post the output of -
```
egrep -i 'bluetooth|btusb|ehci' /var/log/syslog
```

As per the output of usb-devices, the pci bus id is correct, the presence of the link you checked above also confirms that, the only confusion was driver's name, but that is now confirmed as well.... so I am a bit lost. Maybe it is just because I am not able to focus properly, let's hope the logs can help us getting to the correct point.

I hate to give up on something simple like this, but the time required to dig deeper is a big problem for me currently. Hope you won't mind the delays that may occur.

---

### Post by chilabot on 2014-02-16
I have the same problem, here's my output:

robert@robert-laptop: ~$ egrep -i 'bluetooth|btusb|ehci' /var/log/syslog

    Feb 16 10:01:44 robert-laptop kernel: [    1.017224] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
    Feb 16 10:01:44 robert-laptop kernel: [    1.017227] ehci-pci: EHCI PCI platform driver
    Feb 16 10:01:44 robert-laptop kernel: [    1.017437] ehci-pci 0000:00:1a.0: setting latency timer to 64
    Feb 16 10:01:44 robert-laptop kernel: [    1.017454] ehci-pci 0000:00:1a.0: EHCI Host Controller
    Feb 16 10:01:44 robert-laptop kernel: [    1.017462] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
    Feb 16 10:01:44 robert-laptop kernel: [    1.017483] ehci-pci 0000:00:1a.0: debug port 2
    Feb 16 10:01:44 robert-laptop kernel: [    1.021456] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
    Feb 16 10:01:44 robert-laptop kernel: [    1.021482] ehci-pci 0000:00:1a.0: irq 16, io mem 0xd4405c00
    Feb 16 10:01:44 robert-laptop kernel: [    1.032275] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
    Feb 16 10:01:44 robert-laptop kernel: [    1.032323] usb usb1: Product: EHCI Host Controller
    Feb 16 10:01:44 robert-laptop kernel: [    1.032325] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
    Feb 16 10:01:44 robert-laptop kernel: [    1.032804] ehci-pci 0000:00:1d.0: setting latency timer to 64
    Feb 16 10:01:44 robert-laptop kernel: [    1.032814] ehci-pci 0000:00:1d.0: EHCI Host Controller
    Feb 16 10:01:44 robert-laptop kernel: [    1.032820] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
    Feb 16 10:01:44 robert-laptop kernel: [    1.032837] ehci-pci 0000:00:1d.0: debug port 2
    Feb 16 10:01:44 robert-laptop kernel: [    1.036800] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
    Feb 16 10:01:44 robert-laptop kernel: [    1.036819] ehci-pci 0000:00:1d.0: irq 23, io mem 0xd4405800
    Feb 16 10:01:44 robert-laptop kernel: [    1.048284] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
    Feb 16 10:01:44 robert-laptop kernel: [    1.048322] usb usb2: Product: EHCI Host Controller
    Feb 16 10:01:44 robert-laptop kernel: [    1.048325] usb usb2: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
    Feb 16 10:01:44 robert-laptop kernel: [    1.048596] ehci-platform: EHCI generic platform driver
    Feb 16 10:01:44 robert-laptop kernel: [    1.344387] usb 1-1: new high-speed USB device number 2 using ehci-pci
    Feb 16 10:01:44 robert-laptop kernel: [    1.588477] usb 2-1: new high-speed USB device number 2 using ehci-pci
    Feb 16 10:01:44 robert-laptop kernel: [    1.792563] usb 1-1.4: new full-speed USB device number 3 using ehci-pci
    Feb 16 10:01:44 robert-laptop kernel: [    1.960724] usb 1-1.6: new high-speed USB device number 4 using ehci-pci
    Feb 16 10:01:44 robert-laptop kernel: [    2.140573] usb 2-1.1: new low-speed USB device number 3 using ehci-pci
    Feb 16 10:01:44 robert-laptop kernel: [    2.308611] usb 2-1.5: new high-speed USB device number 4 using ehci-pci
    Feb 16 10:01:44 robert-laptop kernel: [   32.254879] Bluetooth: Core ver 2.16
    Feb 16 10:01:44 robert-laptop kernel: [   32.254912] Bluetooth: HCI device and connection manager initialized
    Feb 16 10:01:44 robert-laptop kernel: [   32.254926] Bluetooth: HCI socket layer initialized
    Feb 16 10:01:44 robert-laptop kernel: [   32.254930] Bluetooth: L2CAP socket layer initialized
    Feb 16 10:01:44 robert-laptop kernel: [   32.254940] Bluetooth: SCO socket layer initialized
    Feb 16 10:01:44 robert-laptop kernel: [   32.260291] usbcore: registered new interface driver btusb
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Bluetooth daemon 4.101
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Starting SDP server
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: DIS cannot start: GATT is disabled
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Failed to init deviceinfo plugin
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Failed to init proximity plugin
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Failed to init time plugin
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Failed to init alert plugin
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Failed to init thermometer plugin
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Failed to init gatt_example plugin
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Bluetooth Management interface initialized
    Feb 16 10:01:44 robert-laptop kernel: [   37.090956] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
    Feb 16 10:01:44 robert-laptop kernel: [   37.090964] Bluetooth: BNEP filters: protocol multicast
    Feb 16 10:01:44 robert-laptop kernel: [   37.090982] Bluetooth: BNEP socket layer initialized
    Feb 16 10:01:44 robert-laptop kernel: [   37.095048] Bluetooth: RFCOMM TTY layer initialized
    Feb 16 10:01:44 robert-laptop kernel: [   37.095069] Bluetooth: RFCOMM socket layer initialized
    Feb 16 10:01:44 robert-laptop kernel: [   37.095072] Bluetooth: RFCOMM ver 1.11
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Adapter /org/bluez/727/hci0 has been enabled
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: Unknown command complete for opcode 19
    Feb 16 10:01:44 robert-laptop bluetoothd[727]: hci0: Get Connections (0x0015) failed: Not Powered (0x0f)
    Feb 16 10:01:56 robert-laptop bluetoothd[727]: Endpoint registered: sender=:1.39 path=/MediaEndpoint/HFPAG
    Feb 16 10:01:56 robert-laptop bluetoothd[727]: Endpoint registered: sender=:1.39 path=/MediaEndpoint/HFPHS
    Feb 16 10:01:56 robert-laptop bluetoothd[727]: Endpoint registered: sender=:1.39 path=/MediaEndpoint/A2DPSource
    Feb 16 10:01:56 robert-laptop bluetoothd[727]: Endpoint registered: sender=:1.39 path=/MediaEndpoint/A2DPSink
    Feb 16 10:02:02 robert-laptop bluetoothd[727]: Endpoint registered: sender=:1.58 path=/MediaEndpoint/HFPAG
    Feb 16 10:02:02 robert-laptop bluetoothd[727]: Endpoint registered: sender=:1.58 path=/MediaEndpoint/HFPHS
    Feb 16 10:02:02 robert-laptop bluetoothd[727]: Endpoint registered: sender=:1.58 path=/MediaEndpoint/A2DPSource
    Feb 16 10:02:02 robert-laptop bluetoothd[727]: Endpoint registered: sender=:1.58 path=/MediaEndpoint/A2DPSink
    Feb 16 10:02:19 robert-laptop bluetoothd[727]: Endpoint unregistered: sender=:1.39 path=/MediaEndpoint/HFPAG
    Feb 16 10:02:19 robert-laptop bluetoothd[727]: Endpoint unregistered: sender=:1.39 path=/MediaEndpoint/HFPHS
    Feb 16 10:02:19 robert-laptop bluetoothd[727]: Endpoint unregistered: sender=:1.39 path=/MediaEndpoint/A2DPSource
    Feb 16 10:02:19 robert-laptop bluetoothd[727]: Endpoint unregistered: sender=:1.39 path=/MediaEndpoint/A2DPSink
    Feb 16 10:02:26 robert-laptop bluetoothd[727]: Endpoint unregistered: sender=:1.58 path=/MediaEndpoint/HFPAG
    Feb 16 10:02:26 robert-laptop bluetoothd[727]: Endpoint unregistered: sender=:1.58 path=/MediaEndpoint/HFPHS
    Feb 16 10:02:26 robert-laptop bluetoothd[727]: Endpoint unregistered: sender=:1.58 path=/MediaEndpoint/A2DPSource
    Feb 16 10:02:26 robert-laptop bluetoothd[727]: Endpoint unregistered: sender=:1.58 path=/MediaEndpoint/A2DPSink
    Feb 16 10:02:29 robert-laptop bluetoothd[727]: Discovery session 0x7f397bba87e0 with :1.78 activated
    Feb 16 10:02:29 robert-laptop bluetoothd[727]: hci0: Start Discovery (0x0023) failed: Not Powered (0x0f)
    Feb 16 10:02:29 robert-laptop kernel: [   81.664588] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
    Feb 16 10:02:29 robert-laptop kernel: [   81.664610] Bluetooth: HIDP socket layer initialized
    Feb 16 10:02:44 robert-laptop bluetoothd[727]: Discovery session 0x7f397bba4970 with :1.79 activated
    Feb 16 10:02:44 robert-laptop bluetoothd[727]: hci0: Start Discovery (0x0023) failed: Not Powered (0x0f)


BT works fine in Windows, but in Ubuntu 13.10, after having turned it off once, it stopped working.

---

### Post by gavigan-ryan on 2014-03-13
I don't want to derail this thread, but I've had virtually the same problem. Short background, my Kudu Professional came with 13.10 out of the box and bluetooth worked initially just fine. At some point it stopped, but I was previously able to fix it byusing 
```
 rfkill unblock [index] 
```
That isn't working, but I've followed and gone through all of the same steps as above. I attempted the unbind/bind operations which executed. I don't understand what the problem is, but I think it must be similar. Anyway, here's my output for above command...
```
Mar 13 08:32:23 Kudu-Professional kernel: [38682.006867] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPIMar 13 08:32:23 Kudu-Professional kernel: [38682.022940] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
Mar 13 08:32:23 Kudu-Professional kernel: [38682.881651] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
Mar 13 08:32:23 Kudu-Professional kernel: [38682.913683] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
Mar 13 08:32:23 Kudu-Professional kernel: [38682.994079] ehci-pci 0000:00:1a.0: setting latency timer to 64
Mar 13 08:32:23 Kudu-Professional kernel: [38682.994197] ehci-pci 0000:00:1d.0: setting latency timer to 64
Mar 13 08:32:23 Kudu-Professional kernel: [38683.283213] btusb 3-7:1.0: no reset_resume for driver btusb?
Mar 13 08:32:23 Kudu-Professional kernel: [38683.283214] btusb 3-7:1.1: no reset_resume for driver btusb?
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Unregister path: /org/bluez/806/hci0
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Endpoint unregistered: sender=:1.67 path=/MediaEndpoint/A2DPSink
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Endpoint unregistered: sender=:1.67 path=/MediaEndpoint/A2DPSource
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Endpoint unregistered: sender=:1.67 path=/MediaEndpoint/HFPAG
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Endpoint unregistered: sender=:1.67 path=/MediaEndpoint/HFPHS
Mar 13 08:32:23 Kudu-Professional kernel: [38684.273575] Bluetooth: hci0: read Intel version: 370710018002030d00
Mar 13 08:32:23 Kudu-Professional kernel: [38684.273580] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
Mar 13 08:32:23 Kudu-Professional kernel: [38684.392670] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Adapter /org/bluez/806/hci0 has been enabled
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Unknown command complete for opcode 19
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: hci0: Set Discoverable (0x0006) failed: Busy (0x0a)
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/HFPAG
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/HFPHS
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSource
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSink
Mar 13 08:32:23 Kudu-Professional bluetoothd[806]: hci0: Set Secure Simple Pairing (0x000b) failed: Busy (0x0a)
Mar 13 09:38:29 Kudu-Professional bluetoothd[806]: Host is down (112)
Mar 13 09:38:41 Kudu-Professional pulseaudio[2134]: [pulseaudio] module-bluetooth-device.c: Failed to acquire transport /org/bluez/806/hci0/dev_00_1D_DF_51_DF_2D/fd1
Mar 13 09:38:41 Kudu-Professional kernel: [42667.690059] bluetoothd[806]: segfault at 8 ip 00007f717851b381 sp 00007fffd2ee1570 error 4 in bluetoothd[7f71784e7000+d4000]
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Bluetooth daemon 4.101
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Starting SDP server
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: DIS cannot start: GATT is disabled
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Failed to init deviceinfo plugin
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Failed to init proximity plugin
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Failed to init time plugin
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Failed to init alert plugin
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Failed to init thermometer plugin
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Failed to init gatt_example plugin
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Bluetooth Management interface initialized
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Adapter /org/bluez/4675/hci0 has been enabled
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Unknown command complete for opcode 19
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/HFPAG
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/HFPHS
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSource
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSink
Mar 13 09:38:41 Kudu-Professional bluetoothd[4675]: hci0: Set Secure Simple Pairing (0x000b) failed: Busy (0x0a)
Mar 13 09:38:42 Kudu-Professional bluetoothd[4675]: Authorization request for non-connected device!?
Mar 13 09:38:46 Kudu-Professional bluetoothd[4675]: /org/bluez/4675/hci0/dev_00_1D_DF_51_DF_2D/fd0: fd(27) ready
Mar 13 09:39:16 Kudu-Professional bluetoothd[4675]: Adapter /org/bluez/4675/hci0 has been disabled
Mar 13 09:41:12 Kudu-Professional bluetoothd[4675]: connect: No route to host (113)
Mar 13 09:41:16 Kudu-Professional bluetoothd[4675]: hci0: Set Powered (0x0005) failed: <unknown status> (0x12)
Mar 13 09:41:39 Kudu-Professional bluetoothd[4675]: connect: No route to host (113)
Mar 13 09:42:51  bluetoothd[4675]: last message repeated 6 times
Mar 13 09:43:04  bluetoothd[4675]: last message repeated 2 times
Mar 13 09:43:49 Kudu-Professional kernel: [    0.492960] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 13 09:43:49 Kudu-Professional kernel: [    0.492961] ehci-pci: EHCI PCI platform driver
Mar 13 09:43:49 Kudu-Professional kernel: [    0.493024] ehci-pci 0000:00:1a.0: setting latency timer to 64
Mar 13 09:43:49 Kudu-Professional kernel: [    0.493030] ehci-pci 0000:00:1a.0: EHCI Host Controller
Mar 13 09:43:49 Kudu-Professional kernel: [    0.493034] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
Mar 13 09:43:49 Kudu-Professional kernel: [    0.493045] ehci-pci 0000:00:1a.0: debug port 2
Mar 13 09:43:49 Kudu-Professional kernel: [    0.496956] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
Mar 13 09:43:49 Kudu-Professional kernel: [    0.496968] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7f1c000
Mar 13 09:43:49 Kudu-Professional kernel: [    0.511027] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Mar 13 09:43:49 Kudu-Professional kernel: [    0.511041] usb usb1: Product: EHCI Host Controller
Mar 13 09:43:49 Kudu-Professional kernel: [    0.511042] usb usb1: Manufacturer: Linux 3.11.0-18-generic ehci_hcd
Mar 13 09:43:49 Kudu-Professional kernel: [    0.511224] ehci-pci 0000:00:1d.0: setting latency timer to 64
Mar 13 09:43:49 Kudu-Professional kernel: [    0.511229] ehci-pci 0000:00:1d.0: EHCI Host Controller
Mar 13 09:43:49 Kudu-Professional kernel: [    0.511232] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
Mar 13 09:43:49 Kudu-Professional kernel: [    0.511241] ehci-pci 0000:00:1d.0: debug port 2
Mar 13 09:43:49 Kudu-Professional kernel: [    0.515138] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
Mar 13 09:43:49 Kudu-Professional kernel: [    0.515148] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7f1b000
Mar 13 09:43:49 Kudu-Professional kernel: [    0.527047] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Mar 13 09:43:49 Kudu-Professional kernel: [    0.527057] usb usb2: Product: EHCI Host Controller
Mar 13 09:43:49 Kudu-Professional kernel: [    0.527058] usb usb2: Manufacturer: Linux 3.11.0-18-generic ehci_hcd
Mar 13 09:43:49 Kudu-Professional kernel: [    0.527176] ehci-platform: EHCI generic platform driver
Mar 13 09:43:49 Kudu-Professional kernel: [    0.823441] usb 1-1: new high-speed USB device number 2 using ehci-pci
Mar 13 09:43:49 Kudu-Professional kernel: [    1.067714] usb 2-1: new high-speed USB device number 2 using ehci-pci
Mar 13 09:43:49 Kudu-Professional kernel: [    4.520370] Bluetooth: Core ver 2.16
Mar 13 09:43:49 Kudu-Professional kernel: [    4.520385] Bluetooth: HCI device and connection manager initialized
Mar 13 09:43:49 Kudu-Professional kernel: [    4.520392] Bluetooth: HCI socket layer initialized
Mar 13 09:43:49 Kudu-Professional kernel: [    4.520394] Bluetooth: L2CAP socket layer initialized
Mar 13 09:43:49 Kudu-Professional kernel: [    4.520398] Bluetooth: SCO socket layer initialized
Mar 13 09:43:49 Kudu-Professional kernel: [    4.522569] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 13 09:43:49 Kudu-Professional kernel: [    4.522571] Bluetooth: BNEP filters: protocol multicast
Mar 13 09:43:49 Kudu-Professional kernel: [    4.522576] Bluetooth: BNEP socket layer initialized
Mar 13 09:43:49 Kudu-Professional kernel: [    4.531153] Bluetooth: RFCOMM TTY layer initialized
Mar 13 09:43:49 Kudu-Professional kernel: [    4.531163] Bluetooth: RFCOMM socket layer initialized
Mar 13 09:43:49 Kudu-Professional kernel: [    4.531164] Bluetooth: RFCOMM ver 1.11
Mar 13 10:09:23 Kudu-Professional kernel: [ 1540.765077] ehci-pci 0000:00:1a.0: remove, state 4
Mar 13 10:09:23 Kudu-Professional kernel: [ 1540.769299] ehci-pci 0000:00:1a.0: USB bus 1 deregistered
Mar 13 10:09:53 Kudu-Professional kernel: [ 1570.776339] ehci-pci 0000:00:1a.0: setting latency timer to 64
Mar 13 10:09:53 Kudu-Professional kernel: [ 1570.776349] ehci-pci 0000:00:1a.0: EHCI Host Controller
Mar 13 10:09:53 Kudu-Professional kernel: [ 1570.776354] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
Mar 13 10:09:53 Kudu-Professional kernel: [ 1570.776366] ehci-pci 0000:00:1a.0: debug port 2
Mar 13 10:09:53 Kudu-Professional kernel: [ 1570.780284] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
Mar 13 10:09:53 Kudu-Professional kernel: [ 1570.780295] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7f1c000
Mar 13 10:09:53 Kudu-Professional kernel: [ 1570.788722] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Mar 13 10:09:53 Kudu-Professional kernel: [ 1570.788759] usb usb1: Product: EHCI Host Controller
Mar 13 10:09:53 Kudu-Professional kernel: [ 1570.788760] usb usb1: Manufacturer: Linux 3.11.0-18-generic ehci_hcd
Mar 13 10:09:53 Kudu-Professional kernel: [ 1571.101146] usb 1-1: new high-speed USB device number 2 using ehci-pci



```

---

### Post by MopedTobias on 2014-03-15
Hi,
I have got a quite similar problem, but I think when I installed 13.10 bluetooth initially worked. Then I wasn't able to turn it off by default on startup and I figured something out. But now I donot know any more, what it was what I figured out and am not able to turn it on again.

Ubuntu 13.10 on Lenovo Thinkpad Edge E320

Regards, Timo

---

### Post by pkadeel on 2014-03-21
When I first migrated from windows to Ubuntu 12.04 64bit, I also had bluetooth problem. Everything seemed normal yet I was unable to discover/connect my laptop with other devices. I found a solution on these forums and I remember that the solution provider mentioned that somehow bluetooth device gets turned off in Linux. It made sense to me because back then, I had tested many distros before choosing ubuntu. The solution was
```
sudo bccmd psset -s 0x0000 0x028c 0x0001
```

Later on, I discovered further that when I turn off bluetooth from the bluetooth manager (I don't know its exact name) and then try to turn it on after few days (which involves many shutdown and bootup cycles), it shows same behaviour untill I use the above mentioned command after which I starts working normally. This problem does not occur if I keep bluetooth On during shutdown/bootup cycles.

EDIT: I forgot to mention that I am using Ralink RT3090 combo card (Wifi+bluetooth)

---

### Post by ssameer on 2014-03-22
I tried this solution, but it seems restricted to CSR bluetooth devices only. I get an unsupported manufacturer error. Is there a bug filed for this?

PS: I have the same issue. My laptop is Thinkpad T-400 running Kubuntu 13.10 64 bit. The bluetooth controller is Broadcom Corp. BCM2045B (BDC-2.1).

> **pkadeel said:**
> When I first migrated from windows to Ubuntu 12.04 64bit, I also had bluetooth problem. Everything seemed normal yet I was unable to discover/connect my laptop with other devices. I found a solution on these forums and I remember that the solution provider mentioned that somehow bluetooth device gets turned off in Linux. It made sense to me because back then, I had tested many distros before choosing ubuntu. The solution was
```
sudo bccmd psset -s 0x0000 0x028c 0x0001
```

Later on, I discovered further that when I turn off bluetooth from the bluetooth manager (I don't know its exact name) and then try to turn it on after few days (which involves many shutdown and bootup cycles), it shows same behaviour untill I use the above mentioned command after which I starts working normally. This problem does not occur if I keep bluetooth On during shutdown/bootup cycles.

EDIT: I forgot to mention that I am using Ralink RT3090 combo card (Wifi+bluetooth)

---

### Post by eckhofer on 2014-05-07
I've had the same errors in syslog
```
hci0: Start Discovery (0x0023) failed: Not Powered (0x0f)
```

For me, the problem was solved using
```
sudo hciconfig hci0 up
```

If anybody has the time to file a proper bug report, please link it here. I don't have time for that right now.

---

