---
title: "Logitech diNovo edge - no go again after last LTS 12.04 upgrade"
date: 2014-04-12
forum: Installation &amp; Upgrades
---

### Post by lptr on 2014-04-12
Slowly this is getting an endless story. Again having problems with diNovo Edge. This time since recent upgrade patches and after reboot. Before keyboard worked seamless. After reboot it is dead like I had it several times in the past. 

Anyone with same experiences? Any workarounds there?

Thanks in advance.

---

### Post by lptr on 2014-04-12
Workaround is the same as in the past: 
$ cd /lib/udev/rules.d/
$ sudo nano 97-bluetooth-hid2hci.rules

Look for a line like this:
# Logitech devices
KERNEL=="[COLOR=red]**hiddev**[/COLOR]*", ...

replace this with 
KERNEL=="[COLOR=red]**hidraw**[/COLOR]", ....

and keyboard is back. Note: This file will be replaced without ask during 'some' system updates. This update replaced the file and so the problem with this keyboard was back.

---

### Post by Hammi on 2014-04-14
If I may join in here:

I had the same issue, and the hint did help me - so thanks for that!

However, it's still not working reliably. When I "plug in" the keyboard (and mouse) again (actually, the ubuntu machine is connected to a switch, so this "plug in" is switching back to the ubuntu machine), I get error messages, but no working Logitech device:

```
Apr 14 07:36:06 alpha kernel: [72175.341673] usb 3-1.4: USB disconnect, device number 26
Apr 14 07:36:06 alpha kernel: [72175.597236] usb 3-1.3: USB disconnect, device number 19
Apr 14 07:36:06 alpha kernel: [72176.108411] usb 3-1.1: USB disconnect, device number 18
Apr 14 07:36:06 alpha kernel: [72176.108414] usb 3-1.1.2: USB disconnect, device number 20
Apr 14 07:36:06 alpha kernel: [72176.162059] usb 3-1.1.3: USB disconnect, device number 21
Apr 14 07:36:09 alpha kernel: [72178.877353] usb 3-1.4: new full-speed USB device number 27 using xhci_hcd
Apr 14 07:36:09 alpha kernel: [72178.898270] usb 3-1.4: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
Apr 14 07:36:09 alpha kernel: [72178.899323] hub 3-1.4:1.0: USB hub found
Apr 14 07:36:09 alpha kernel: [72178.899449] hub 3-1.4:1.0: 4 ports detected
Apr 14 07:36:09 alpha kernel: [72179.168892] usb 3-1.4.1: new low-speed USB device number 28 using xhci_hcd
Apr 14 07:36:09 alpha mtp-probe: checking bus 3, device 28: "/sys/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/usb3/3-1/3-1.4/3-1.4.1"
Apr 14 07:36:09 alpha kernel: [72179.258223] logitech-djreceiver 0003:046D:C52B.001E: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:07:00.0-1.4.1/input2
Apr 14 07:36:09 alpha kernel: [72179.260462] logitech-djreceiver 0003:046D:C52B.001E: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
Apr 14 07:36:09 alpha mtp-probe: bus: 3, device: 28 was not an MTP device
Apr 14 07:36:09 alpha kernel: [72179.260846] logitech-djreceiver: probe of 0003:046D:C52B.001E failed with error -32
Apr 14 07:36:10 alpha kernel: [72179.720262] pctv452e: I2C error -121; AA D6  CC 00 01 -> 55 D6  CC 00 00.
Apr 14 07:36:11 alpha kernel: [72181.220110] usb 3-1.4: USB disconnect, device number 27
Apr 14 07:36:11 alpha kernel: [72181.220113] usb 3-1.4.1: USB disconnect, device number 28
Apr 14 07:36:14 alpha kernel: [72183.988651] usb 3-1.4: new full-speed USB device number 29 using xhci_hcd
Apr 14 07:36:14 alpha kernel: [72184.009553] usb 3-1.4: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
Apr 14 07:36:14 alpha kernel: [72184.010653] hub 3-1.4:1.0: USB hub found
Apr 14 07:36:14 alpha kernel: [72184.010777] hub 3-1.4:1.0: 4 ports detected
Apr 14 07:36:14 alpha kernel: [72184.280205] usb 3-1.4.1: new low-speed USB device number 30 using xhci_hcd
Apr 14 07:36:15 alpha mtp-probe: checking bus 3, device 30: "/sys/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/usb3/3-1/3-1.4/3-1.4.1"
Apr 14 07:36:15 alpha kernel: [72184.383446] logitech-djreceiver 0003:046D:C52B.0021: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:07:00.0-1.4.1/input2
Apr 14 07:36:15 alpha mtp-probe: bus: 3, device: 30 was not an MTP device
Apr 14 07:36:15 alpha kernel: [72184.385597] logitech-djreceiver 0003:046D:C52B.0021: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
Apr 14 07:36:15 alpha kernel: [72184.385960] logitech-djreceiver: probe of 0003:046D:C52B.0021 failed with error -32
Apr 14 07:36:17 alpha kernel: [72186.843034] usb 3-1.4: USB disconnect, device number 29
Apr 14 07:36:17 alpha kernel: [72186.843037] usb 3-1.4.1: USB disconnect, device number 30
Apr 14 07:36:20 alpha kernel: [72189.615029] usb 3-1.4: new full-speed USB device number 31 using xhci_hcd
Apr 14 07:36:20 alpha kernel: [72189.635968] usb 3-1.4: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
Apr 14 07:36:20 alpha kernel: [72189.637091] hub 3-1.4:1.0: USB hub found
Apr 14 07:36:20 alpha kernel: [72189.637224] hub 3-1.4:1.0: 4 ports detected
Apr 14 07:36:20 alpha kernel: [72189.906587] usb 3-1.4.1: new low-speed USB device number 32 using xhci_hcd
Apr 14 07:36:20 alpha mtp-probe: checking bus 3, device 32: "/sys/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/usb3/3-1/3-1.4/3-1.4.1"
Apr 14 07:36:20 alpha kernel: [72190.008790] logitech-djreceiver 0003:046D:C52B.0024: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:07:00.0-1.4.1/input2
Apr 14 07:36:20 alpha mtp-probe: bus: 3, device: 32 was not an MTP device
Apr 14 07:36:20 alpha kernel: [72190.011118] logitech-djreceiver 0003:046D:C52B.0024: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
Apr 14 07:36:20 alpha kernel: [72190.011555] logitech-djreceiver: probe of 0003:046D:C52B.0024 failed with error -32
Apr 14 07:36:23 alpha kernel: [72192.465890] usb 3-1.4: USB disconnect, device number 31
Apr 14 07:36:23 alpha kernel: [72192.465893] usb 3-1.4.1: USB disconnect, device number 32
Apr 14 07:36:25 alpha kernel: [72195.237460] usb 3-1.4: new full-speed USB device number 33 using xhci_hcd
Apr 14 07:36:25 alpha kernel: [72195.258356] usb 3-1.4: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
Apr 14 07:36:25 alpha kernel: [72195.259412] hub 3-1.4:1.0: USB hub found
Apr 14 07:36:25 alpha kernel: [72195.259538] hub 3-1.4:1.0: 4 ports detected
Apr 14 07:36:26 alpha kernel: [72195.529007] usb 3-1.4.1: new low-speed USB device number 34 using xhci_hcd
Apr 14 07:36:26 alpha mtp-probe: checking bus 3, device 34: "/sys/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/usb3/3-1/3-1.4/3-1.4.1"
Apr 14 07:36:26 alpha mtp-probe: bus: 3, device: 34 was not an MTP device
Apr 14 07:36:26 alpha kernel: [72195.629551] logitech-djreceiver 0003:046D:C52B.0027: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:07:00.0-1.4.1/input2
Apr 14 07:36:26 alpha kernel: [72195.631896] logitech-djreceiver 0003:046D:C52B.0027: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
Apr 14 07:36:26 alpha kernel: [72195.632256] logitech-djreceiver: probe of 0003:046D:C52B.0027 failed with error -32
Apr 14 07:36:28 alpha kernel: [72198.088800] usb 3-1.4: USB disconnect, device number 33
Apr 14 07:36:28 alpha kernel: [72198.088803] usb 3-1.4.1: USB disconnect, device number 34
Apr 14 07:36:31 alpha kernel: [72200.604293] usb 3-1.4: new full-speed USB device number 35 using xhci_hcd
Apr 14 07:36:31 alpha kernel: [72200.625198] usb 3-1.4: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
Apr 14 07:36:31 alpha kernel: [72200.626309] hub 3-1.4:1.0: USB hub found
Apr 14 07:36:31 alpha kernel: [72200.626459] hub 3-1.4:1.0: 4 ports detected
Apr 14 07:36:31 alpha kernel: [72200.895818] usb 3-1.4.1: new low-speed USB device number 36 using xhci_hcd
Apr 14 07:36:31 alpha mtp-probe: checking bus 3, device 36: "/sys/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/usb3/3-1/3-1.4/3-1.4.1"
Apr 14 07:36:31 alpha kernel: [72200.995560] logitech-djreceiver 0003:046D:C52B.002A: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:07:00.0-1.4.1/input2
Apr 14 07:36:31 alpha mtp-probe: bus: 3, device: 36 was not an MTP device
Apr 14 07:36:31 alpha kernel: [72200.998447] logitech-djreceiver 0003:046D:C52B.002A: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
Apr 14 07:36:31 alpha kernel: [72200.998805] logitech-djreceiver: probe of 0003:046D:C52B.002A failed with error -32
```

---

### Post by lptr on 2014-04-14
Just a shot in the dark: Seems this an USB 3 hub? Or at least USB 3 is in the chain. 
I am using my diNovo edge at an USB 2 hub. Disconnect/reconnect working seamless (recently tested because of your request). I've heard that some USB 3 devices causing problems (not only in conjunction with Ubuntu). Maybe your BIOS making trouble. You may also try to temporarily disable USB 3 support in BIOS for testing. Could be a timing problem or some other glitch driver wise... give that a try and let us know.

---

### Post by Hammi on 2014-04-16
Thanks, the hint at USB3 was great. I had indeed, when the problems occurred, thought that maybe something with the USB ports had gone wrong, and had tried several different port. I now plugged the keyboard back into a USB 2 port, and it's working fine again.

Thank you!

---

### Post by lptr on 2014-04-18
No problem. You're welcome :)

---

### Post by Hammi on 2014-04-19
That joy didn't last for too long:

```
Apr 19 08:16:02 alpha kernel: [53605.564136] usb 2-1.3.4: new full-speed USB device number 42 using ehci_hcd
Apr 19 08:16:02 alpha kernel: [53605.672997] hub 2-1.3.4:1.0: USB hub found
Apr 19 08:16:02 alpha kernel: [53605.673192] hub 2-1.3.4:1.0: 4 ports detected
Apr 19 08:16:46 alpha kernel: [53650.071734] usb 2-1.3.4: USB disconnect, device number 42
Apr 19 08:16:46 alpha kernel: [53650.327289] usb 2-1.3.3: USB disconnect, device number 37
Apr 19 08:16:47 alpha kernel: [53650.838513] usb 2-1.3.1: USB disconnect, device number 34
Apr 19 08:16:47 alpha kernel: [53650.838516] usb 2-1.3.1.2: USB disconnect, device number 35
Apr 19 08:16:47 alpha kernel: [53650.866857] usb 2-1.3.1.3: USB disconnect, device number 36
Apr 19 08:16:50 alpha kernel: [53653.606234] usb 2-1.3.4: new full-speed USB device number 43 using ehci_hcd
Apr 19 08:16:50 alpha kernel: [53653.714798] hub 2-1.3.4:1.0: USB hub found
Apr 19 08:16:50 alpha kernel: [53653.715021] hub 2-1.3.4:1.0: 4 ports detected
Apr 19 08:16:50 alpha kernel: [53653.985556] usb 2-1.3.4.1: new full-speed USB device number 44 using ehci_hcd
Apr 19 08:16:50 alpha mtp-probe: checking bus 2, device 44: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.4/2-1.3.4.1"
Apr 19 08:16:50 alpha kernel: [53654.152110] logitech-djreceiver 0003:046D:C52B.0023: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.3.4.1/input2
Apr 19 08:16:50 alpha mtp-probe: bus: 2, device: 44 was not an MTP device
Apr 19 08:16:50 alpha kernel: [53654.154133] logitech-djreceiver 0003:046D:C52B.0023: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
Apr 19 08:16:50 alpha kernel: [53654.154260] logitech-djreceiver: probe of 0003:046D:C52B.0023 failed with error -32
Apr 19 08:16:52 alpha kernel: [53656.205207] usb 2-1.3.4: USB disconnect, device number 43
Apr 19 08:16:52 alpha kernel: [53656.205211] usb 2-1.3.4.1: USB disconnect, device number 44
Apr 19 08:16:55 alpha kernel: [53658.973031] usb 2-1.3.4: new full-speed USB device number 45 using ehci_hcd
Apr 19 08:16:55 alpha kernel: [53659.081659] hub 2-1.3.4:1.0: USB hub found
Apr 19 08:16:55 alpha kernel: [53659.081863] hub 2-1.3.4:1.0: 4 ports detected
Apr 19 08:16:55 alpha kernel: [53659.352496] usb 2-1.3.4.1: new full-speed USB device number 46 using ehci_hcd
Apr 19 08:16:56 alpha mtp-probe: checking bus 2, device 46: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.4/2-1.3.4.1"
Apr 19 08:16:56 alpha kernel: [53659.535685] logitech-djreceiver 0003:046D:C52B.0027: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.3.4.1/input2
Apr 19 08:16:56 alpha mtp-probe: bus: 2, device: 46 was not an MTP device
Apr 19 08:16:56 alpha kernel: [53659.537674] logitech-djreceiver 0003:046D:C52B.0027: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
Apr 19 08:16:56 alpha kernel: [53659.537757] logitech-djreceiver: probe of 0003:046D:C52B.0027 failed with error -32
Apr 19 08:16:58 alpha kernel: [53661.827328] usb 2-1.3.4: USB disconnect, device number 45
Apr 19 08:16:58 alpha kernel: [53661.827332] usb 2-1.3.4.1: USB disconnect, device number 46
Apr 19 08:17:01 alpha kernel: [53664.595531] usb 2-1.3.4: new full-speed USB device number 47 using ehci_hcd
Apr 19 08:17:01 alpha kernel: [53664.704007] hub 2-1.3.4:1.0: USB hub found
Apr 19 08:17:01 alpha kernel: [53664.704212] hub 2-1.3.4:1.0: 4 ports detected
Apr 19 08:17:01 alpha kernel: [53664.974895] usb 2-1.3.4.1: new full-speed USB device number 48 using ehci_hcd
Apr 19 08:17:01 alpha mtp-probe: checking bus 2, device 48: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.4/2-1.3.4.1"
Apr 19 08:17:01 alpha CRON[1352]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 08:17:01 alpha kernel: [53665.152107] logitech-djreceiver 0003:046D:C52B.002B: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.3.4.1/input2
Apr 19 08:17:01 alpha kernel: [53665.154311] logitech-djreceiver 0003:046D:C52B.002B: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
Apr 19 08:17:01 alpha kernel: [53665.154403] logitech-djreceiver: probe of 0003:046D:C52B.002B failed with error -32
Apr 19 08:17:01 alpha mtp-probe: bus: 2, device: 48 was not an MTP device
Apr 19 08:17:03 alpha kernel: [53667.449603] usb 2-1.3.4: USB disconnect, device number 47
Apr 19 08:17:03 alpha kernel: [53667.449607] usb 2-1.3.4.1: USB disconnect, device number 48
Apr 19 08:17:06 alpha kernel: [53670.217930] usb 2-1.3.4: new full-speed USB device number 49 using ehci_hcd
Apr 19 08:17:06 alpha kernel: [53670.326410] hub 2-1.3.4:1.0: USB hub found
Apr 19 08:17:06 alpha kernel: [53670.326616] hub 2-1.3.4:1.0: 4 ports detected
Apr 19 08:17:07 alpha kernel: [53670.597268] usb 2-1.3.4.1: new full-speed USB device number 50 using ehci_hcd
Apr 19 08:17:07 alpha mtp-probe: checking bus 2, device 50: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.4/2-1.3.4.1"
Apr 19 08:17:07 alpha kernel: [53670.762902] logitech-djreceiver 0003:046D:C52B.002F: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.3.4.1/input2
Apr 19 08:17:07 alpha mtp-probe: bus: 2, device: 50 was not an MTP device
Apr 19 08:17:07 alpha kernel: [53670.773969] logitech-djreceiver 0003:046D:C52B.002F: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
Apr 19 08:17:07 alpha kernel: [53670.774170] logitech-djreceiver: probe of 0003:046D:C52B.002F failed with error -32
Apr 19 08:17:09 alpha kernel: [53673.071831] usb 2-1.3.4: USB disconnect, device number 49
Apr 19 08:17:09 alpha kernel: [53673.071834] usb 2-1.3.4.1: USB disconnect, device number 50
Apr 19 08:17:12 alpha kernel: [53675.572765] usb 2-1.3.4: new full-speed USB device number 51 using ehci_hcd
Apr 19 08:17:12 alpha kernel: [53675.681238] hub 2-1.3.4:1.0: USB hub found
Apr 19 08:17:12 alpha kernel: [53675.681430] hub 2-1.3.4:1.0: 4 ports detected
Apr 19 08:17:12 alpha kernel: [53675.952107] usb 2-1.3.4.1: new full-speed USB device number 52 using ehci_hcd
Apr 19 08:17:12 alpha mtp-probe: checking bus 2, device 52: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.4/2-1.3.4.1"
Apr 19 08:17:12 alpha kernel: [53676.122841] logitech-djreceiver 0003:046D:C52B.0033: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.3.4.1/input2
Apr 19 08:17:12 alpha mtp-probe: bus: 2, device: 52 was not an MTP device
Apr 19 08:17:12 alpha kernel: [53676.124789] logitech-djreceiver 0003:046D:C52B.0033: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
Apr 19 08:17:12 alpha kernel: [53676.124923] logitech-djreceiver: probe of 0003:046D:C52B.0033 failed with error -32
```

I.e. the same error occurs with USB 2. :?

You think the hub is the problem? Any suggestion for a DVI/SUB switch that works seamless with Ubuntu?

Or maybe I should try upgrading to 14.04 first... (Only that could break a lot of other things which are working ok... Gee!)

---

### Post by lptr on 2014-04-25
In the past I used ATEN switches. However, I don't know how well they do perform nowadays, as I reduced my own 'device park' here at my office dramatically and so I do not need to use such switches anymore. Sorry!

Oh - another point: Did you control, if your recent changes in the config files are still there? 
This file eventually was overwritten by updates. So if something goes wrong control this, first.

---

### Post by Hammi on 2014-05-26
Yes, the config files were still up to date, and my switch is from ATEN, too. I now exchanged the Logitech keyboard for one from Microsoft, and things are working fine now.

---

