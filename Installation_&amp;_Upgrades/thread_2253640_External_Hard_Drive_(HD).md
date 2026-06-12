---
title: "External Hard Drive (HD)"
date: 2014-11-21
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2014-11-21
Hello everybody,

I installed the Ubuntu 14.10, then I realized that while I plugged in an HDD or USB, it does not appear:

```

# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

```

Thanks in advance

---

### Post by ajgreeny on 2014-11-21
How is the external disk partitioned; what filesystem does it have on it, or is it the same for all external disks?
Plug in an external disk and immediately run ```
dmesg | tail -n 20
``` which will show the final 20 lines of dmesg and may tell us more about the disk plugged in and give a clue as to why it is not mounting, as it should do normally.

---

### Post by alfirdaous on 2014-11-21
It is for all external disks.

```

$ dmesg | tail -n 20
[   27.419803] systemd-logind[1059]: Failed to start user service: Unknown unit: user@112.service
[   27.426507] systemd-logind[1059]: New session c1 of user lightdm.
[   27.426536] systemd-logind[1059]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
[   46.854135] systemd-logind[1059]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   46.854147] systemd-logind[1059]: Failed to start user service: Unknown unit: user@1000.service
[   46.880677] systemd-logind[1059]: New session c2 of user aburayane.
[   46.880721] systemd-logind[1059]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   75.048165] usb 7-2: USB disconnect, device number 2
[   76.564053] usb 7-2: new full-speed USB device number 3 using uhci_hcd
[   76.739072] usb 7-2: New USB device found, idVendor=03f0, idProduct=171d
[   76.739077] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   76.739081] usb 7-2: Product: HP Integrated Module
[   76.739084] usb 7-2: Manufacturer: Broadcom Corp
[  235.976875] perf interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  414.256091] usb 2-1: new high-speed USB device number 5 using ehci-pci
[  414.389404] usb 2-1: New USB device found, idVendor=1058, idProduct=1100
[  414.389412] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  414.389419] usb 2-1: Product: My Book         
[  414.389424] usb 2-1: Manufacturer: Western Digital 
[  414.389430] usb 2-1: SerialNumber: 57442D574341563530383432393735


```

another command:

```

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        27G  4.8G   21G  19% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           301M  960K  300M   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            1.5G  156K  1.5G   1% /run/shm
none            100M   56K  100M   1% /run/user


```

---

### Post by ajgreeny on 2014-11-21
The line in your dmesg output
> perf interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
worries me a bit, but I do not have the knowledge to give you any answers, I'm afraid, and that line appears just before the USB disk is detected, so it may be totally unrelated.

Wait for others who may be able to help you more.

---

### Post by ubfan1 on 2014-11-21
The disk in the enclosure is not being seen, so plug/unplug it a few times to see if you got a bad connection.  Worst case would be there is no disk at all in the box!

---

### Post by ajgreeny on 2014-11-22
The disk ***is*** being seen by the system and shows in the final 6 lines of dmesg; it is simply not mounting for some reason, which is why it is not shown in the "df -h" command.

Does it show if you run **sudo fdisk -l**

---

### Post by ubfan1 on 2014-11-22
A working USB plugin looks like:
> [ 2080.911463] usb 4-2: new SuperSpeed USB device number 2 using xhci_hcd
[ 2080.929747] usb 4-2: New USB device found, idVendor=0480, idProduct=a00d
[ 2080.929754] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2080.929758] usb 4-2: Product: External USB 3.0
[ 2080.929762] usb 4-2: Manufacturer: TOSHIBA
[ 2080.929764] usb 4-2: SerialNumber: 231842205167

====VVV Missing in above example VVV======
[ 2080.977941] usb-storage 4-2:1.0: USB Mass Storage device detected
[ 2080.978149] scsi7 : usb-storage 4-2:1.0
[ 2080.978571] usbcore: registered new interface driver usb-storage
[ 2084.362012] scsi 7:0:0:0: Direct-Access     TOSHIBA  External USB 3.0 5438 PQ: 0 ANSI: 6
[ 2084.362619] sd 7:0:0:0: Attached scsi generic sg3 type 0
[ 2084.364573] sd 7:0:0:0: [sdc] 1953525164 512-byte logical blocks: (1.00 TB/931 GiB)
[ 2084.365006] sd 7:0:0:0: [sdc] Write Protect is off
[ 2084.365008] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 2084.365352] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2084.455142]  sdc: sdc1 sdc2 sdc3 sdc4 sdc5 sdc6
[ 2084.459191] sd 7:0:0:0: [sdc] Attached SCSI disk
[ 2085.397756] EXT4-fs (sdc4): mounted filesystem with ordered data mode. Opts: (null)
[ 2085.480850] EXT4-fs (sdc5): mounted filesystem with ordered data mode. Opts: (null)
[ 2085.636727] EXT4-fs (sdc3): mounted filesystem with ordered data mode. Opts: (null)

Note that the part present in the question is the enclosure "My Book", here is it "External USB 3.0".  The next part is the disk recognition, which is absent totally in the original question.  Think of the USB enclosure as a little hub, with only one thing plugged in.  Maybe that internal disk is not plugged in firmly, so check it, but opening the box may void your warranty.  If you just bought the box, return it.

---

### Post by oldfred on 2014-11-22
Did this drive work before?

Others have had issues:
 Western Digital MyBook - best to totally reformat to remove Windows unique system 
[http://ubuntuforums.org/showthread.php?t=1506476&p=9441162&viewfull=1#post9441162](http://ubuntuforums.org/showthread.php?t=1506476&p=9441162&viewfull=1#post9441162)

---

### Post by alfirdaous on 2014-11-26
I think these kind of problems are only with the release of 14, so I installed 13.10 and it works

---

### Post by sudodus on 2014-11-26
If you want to or have to run a previous Ubuntu version, please run 12.04 LTS (upgrade to 12.04.5 if it works)! This version has long time support until April 2017. The versions 12.10, 13.04 and 13.10 have all passed end of life and receive no security updates.

See also this link [Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.]("http://ubuntuforums.org/showthread.php?t=2229730")

---

