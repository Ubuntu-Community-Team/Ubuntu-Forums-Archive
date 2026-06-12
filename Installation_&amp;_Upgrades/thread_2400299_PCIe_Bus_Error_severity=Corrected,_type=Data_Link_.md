---
title: "PCIe Bus Error: severity=Corrected, type=Data Link Layer on new Desktop install"
date: 2018-09-04
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2018-09-04
Just installed the latest (18.10 LTS) on brand new desktop (see attached spec).

The problem is that the PC hangs after being up for a few hours.

Before rebooting I found many of the following errors

```
Sep  4 22:52:24 inges2 kernel: [11889.915252] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:52:24 inges2 kernel: [11889.915258] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:52:24 inges2 kernel: [11889.915263] pcieport 0000:00:01.2:    [12] Replay Timer Timeout
Sep  4 22:52:27 inges2 kernel: [11893.127616] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:52:27 inges2 kernel: [11893.127626] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:52:27 inges2 kernel: [11893.127632] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:52:27 inges2 kernel: [11893.127636] pcieport 0000:00:01.2:    [12] Replay Timer Timeout
Sep  4 22:52:33 inges2 kernel: [11899.060595] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:52:33 inges2 kernel: [11899.060605] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:52:33 inges2 kernel: [11899.060612] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:52:33 inges2 kernel: [11899.060617] pcieport 0000:00:01.2:    [12] Replay Timer Timeout
Sep  4 22:52:35 inges2 kernel: [11900.898788] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:52:35 inges2 kernel: [11900.898798] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:52:35 inges2 kernel: [11900.898805] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:52:35 inges2 kernel: [11900.898809] pcieport 0000:00:01.2:    [12] Replay Timer Timeout
Sep  4 22:52:36 inges2 kernel: [11901.824599] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:52:36 inges2 kernel: [11901.824608] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:52:36 inges2 kernel: [11901.824616] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:52:36 inges2 kernel: [11901.824620] pcieport 0000:00:01.2:    [12] Replay Timer Timeout
Sep  4 22:52:37 inges2 kernel: [11903.241021] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:52:37 inges2 kernel: [11903.241032] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Receiver ID)
Sep  4 22:52:37 inges2 kernel: [11903.241039] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00000080/00006000
Sep  4 22:52:37 inges2 kernel: [11903.241043] pcieport 0000:00:01.2:    [ 7] Bad DLLP
Sep  4 22:52:38 inges2 kernel: [11904.131122] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:52:38 inges2 kernel: [11904.131132] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:52:38 inges2 kernel: [11904.131139] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:52:38 inges2 kernel: [11904.131144] pcieport 0000:00:01.2:    [12] Replay Timer Timeout
Sep  4 22:52:43 inges2 kernel: [11909.141886] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:52:43 inges2 kernel: [11909.141895] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:52:43 inges2 kernel: [11909.141902] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:52:43 inges2 kernel: [11909.141907] pcieport 0000:00:01.2:    [12] Replay Timer Timeout
Sep  4 22:52:50 inges2 kernel: [11916.470504] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:52:50 inges2 kernel: [11916.470515] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:52:50 inges2 kernel: [11916.470521] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:52:50 inges2 kernel: [11916.470526] pcieport 0000:00:01.2:    [12] Replay Timer Timeout

```

All seems to be on device [1022:15d3

After rebooting this device initially seems to be ok.

```
Sep  4 22:56:51 inges2 kernel: [    0.080847] pci_bus 0000:00: root bus resource [mem 0xfee00000-0xffffffff window]
Sep  4 22:56:51 inges2 kernel: [    0.080848] pci_bus 0000:00: root bus resource [bus 00-ff]
Sep  4 22:56:51 inges2 kernel: [    0.080857] pci 0000:00:00.0: [1022:15d0] type 00 class 0x060000
Sep  4 22:56:51 inges2 kernel: [    0.080984] pci 0000:00:00.2: [1022:15d1] type 00 class 0x080600
Sep  4 22:56:51 inges2 kernel: [    0.081133] pci 0000:00:01.0: [1022:1452] type 00 class 0x060000
Sep  4 22:56:51 inges2 kernel: [    0.081242] pci 0000:00:01.2: [1022:15d3] type 01 class 0x060400
Sep  4 22:56:51 inges2 kernel: [    0.081346] pci 0000:00:01.2: PME# supported from D0 D3hot D3cold
Sep  4 22:56:51 inges2 kernel: [    0.081462] pci 0000:00:08.0: [1022:1452] type 00 class 0x060000
Sep  4 22:56:51 inges2 kernel: [    0.081572] pci 0000:00:08.1: [1022:15db] type 01 class 0x060400
Sep  4 22:56:51 inges2 kernel: [    0.081624] pci 0000:00:08.1: enabling Extended Tags
Sep  4 22:56:51 inges2 kernel: [    0.081680] pci 0000:00:08.1: PME# supported from D0 D3hot D3cold
Sep  4 22:56:51 inges2 kernel: [    0.081768] pci 0000:00:08.2: [1022:15dc] type 01 class 0x060400
Sep  4 22:56:51 inges2 kernel: [    0.081819] pci 0000:00:08.2: enabling Extended Tags
Sep  4 22:56:51 inges2 kernel: [    0.081870] pci 0000:00:08.2: PME# supported from D0 D3hot D3cold
Sep  4 22:56:51 inges2 kernel: [    0.081987] pci 0000:00:14.0: [1022:790b] type 00 class 0x0c0500
Sep  4 22:56:51 inges2 kernel: [    0.082164] pci 0000:00:14.3: [1022:790e] type 00 class 0x060100

```

Until later
```
Sep  4 22:56:51 inges2 kernel: [    0.808498] ehci-platform: EHCI generic platform driver
Sep  4 22:56:51 inges2 kernel: [    0.808502] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep  4 22:56:51 inges2 kernel: [    0.808503] ohci-pci: OHCI PCI platform driver
Sep  4 22:56:51 inges2 kernel: [    0.808508] ohci-platform: OHCI generic platform driver
Sep  4 22:56:51 inges2 kernel: [    0.808511] uhci_hcd: USB Universal Host Controller Interface driver
Sep  4 22:56:51 inges2 kernel: [    0.808609] xhci_hcd 0000:15:00.0: xHCI Host Controller
Sep  4 22:56:51 inges2 kernel: [    0.808613] xhci_hcd 0000:15:00.0: new USB bus registered, assigned bus number 1
Sep  4 22:56:51 inges2 kernel: [    0.812499] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:56:51 inges2 kernel: [    0.812506] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:56:51 inges2 kernel: [    0.812551] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:56:51 inges2 kernel: [    0.812588] pcieport 0000:00:01.2:    [12] Replay Timer Timeout
Sep  4 22:56:51 inges2 kernel: [    0.812615] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:56:51 inges2 kernel: [    0.812627] pcieport 0000:15:00.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=1502(Transmitter ID)
Sep  4 22:56:51 inges2 kernel: [    0.812666] pcieport 0000:15:00.2:   device [1022:43c6] error status/mask=00003000/00002000
Sep  4 22:56:51 inges2 kernel: [    0.812698] pcieport 0000:15:00.2:    [12] Replay Timer Timeout
Sep  4 22:56:51 inges2 kernel: [    0.838643] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:56:51 inges2 kernel: [    0.838650] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:56:51 inges2 kernel: [    0.838698] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:56:51 inges2 kernel: [    0.838736] pcieport 0000:00:01.2:    [12] Replay Timer Timeout
Sep  4 22:56:51 inges2 kernel: [    0.848299] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:56:51 inges2 kernel: [    0.848307] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Transmitter ID)
Sep  4 22:56:51 inges2 kernel: [    0.848376] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00001000/00006000
Sep  4 22:56:51 inges2 kernel: [    0.848429] pcieport 0000:00:01.2:    [12] Replay Timer Timeout
Sep  4 22:56:51 inges2 kernel: [    0.861603] xhci_hcd 0000:15:00.0: hcc params 0x0200ef81 hci version 0x110 quirks 0x00000410
Sep  4 22:56:51 inges2 kernel: [    0.861793] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Sep  4 22:56:51 inges2 kernel: [    0.861795] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep  4 22:56:51 inges2 kernel: [    0.861796] usb usb1: Product: xHCI Host Controller

```

```
Sep  4 22:56:51 inges2 kernel: [    3.397757] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:56:51 inges2 kernel: [    3.399429] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Receiver ID)
Sep  4 22:56:51 inges2 kernel: [    3.400552] random: fast init done
Sep  4 22:56:51 inges2 kernel: [    3.402018] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00000040/00006000
Sep  4 22:56:51 inges2 kernel: [    3.403300] pcieport 0000:00:01.2:    [ 6] Bad TLP
Sep  4 22:56:51 inges2 kernel: [    3.403971] random: systemd-udevd: uninitialized urandom read (16 bytes read)
Sep  4 22:56:51 inges2 kernel: [    3.403980] random: systemd-udevd: uninitialized urandom read (16 bytes read)
Sep  4 22:56:51 inges2 kernel: [    3.403991] random: systemd-udevd: uninitialized urandom read (16 bytes read)
Sep  4 22:56:51 inges2 kernel: [    3.423125] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:56:51 inges2 kernel: [    3.424700] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Receiver ID)
Sep  4 22:56:51 inges2 kernel: [    3.425928] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00000040/00006000
Sep  4 22:56:51 inges2 kernel: [    3.427164] pcieport 0000:00:01.2:    [ 6] Bad TLP
Sep  4 22:56:51 inges2 kernel: [    3.428399] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:56:51 inges2 kernel: [    3.429631] pcieport 0000:15:00.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=1502(Transmitter ID)
Sep  4 22:56:51 inges2 kernel: [    3.430691] pcieport 0000:15:00.2:   device [1022:43c6] error status/mask=00001000/00002000
Sep  4 22:56:51 inges2 kernel: [    3.431678] pcieport 0000:15:00.2:    [12] Replay Timer Timeout
Sep  4 22:56:51 inges2 kernel: [    3.436127] pcieport 0000:00:01.2: AER: Corrected error received: id=0008
Sep  4 22:56:51 inges2 kernel: [    3.437103] pcieport 0000:00:01.2: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=000a(Receiver ID)
Sep  4 22:56:51 inges2 kernel: [    3.438094] pcieport 0000:00:01.2:   device [1022:15d3] error status/mask=00000040/00006000
Sep  4 22:56:51 inges2 kernel: [    3.439081] pcieport 0000:00:01.2:    [ 6] Bad TLP

```

I literally get hundreds of these, but not sure as to the cause (or fix)
Thanks

---

### Post by dsstorefile1 on 2018-09-06
Since you say the desktop is brand-new, the errors are probably benign. Try appending `pci=nomsi` to the kernel command line to silence the error messages.

---

### Post by lister171254 on 2018-09-09
I will try this, but I don't think this is benign as it hangs the machine

---

### Post by lister171254 on 2018-09-09
Have added the suggested switch, but that really hangs the box. Maybe it's go something to do with the ecnrypted disk, but I don't get the prompt for the password when the grub command line looks like this (see attached fails.txt)
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"
```

Without this it boots ok (see normal boot .txt)

---

### Post by lister171254 on 2018-09-19
Attached is the output of 
```
lspci -vv
```

Still logs a large amount of warnings and hangs the machine occasionally

---

### Post by scottstensland on 2018-12-21
Those error will happen when mounting a second disk the wrong way ... do you have multiple drives ?   
If so, the solution involves editing your `/etc/fstab`   

backup current file   `sudo cp /etc/fstab  /etc/fstab~prior.art`

show all partitions by issuing   `sudo blkid`

partial output will look similar to

/dev/sdb7: LABEL="1810v01"  UUID="61450f7b-44bf-429f-951e-6c8c17de5f43" TYPE="ext4"  PARTUUID="2f0454ca-ed4a-4744-9c65-00b5a07a3741"


above is a partition on my second disk I want to auto mount on boot

IMPORTANT - take notice of value of UUID  and TYPE 

now I need to decide what full path I want that to get mounted to on my main drive ... let say I want `/media/aha/1810v01`  so just create this now as it must exist prior to doing the mount

`sudo mkdir -p /media/aha`

`sudo chown aha:ahs /media/aha`

now as myself ( aha ) issue 

`mkdir /media/aha/1810v01`


now add a new line at bottom of `/etc/fstab`  to define the mount as per

`sudo vi /etc/fstab`

 now add following line


`UUID=61450f7b-44bf-429f-951e-6c8c17de5f43   /media/aha/1810v01   ext4  defaults  0  0`


now just reboot and those errors will go away

---

### Post by pebas on 2019-05-16
Bug  was gone (fixed, I think) in my PC today after installing new Kernel  version "linux-image-4.15.0-50-generic" in Ubuntu 18.04.2 x86_64.

---

### Post by muhammetmus on 2019-05-17
Thank You [all]("https://tabletadam.com/")

---

