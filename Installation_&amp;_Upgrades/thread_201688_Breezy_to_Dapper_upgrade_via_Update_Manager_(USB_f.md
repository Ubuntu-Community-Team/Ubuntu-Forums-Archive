---
title: "Breezy to Dapper upgrade via Update Manager (USB flash problem, partitially solved)"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by gray380 on 2006-06-22
Hi All,

Before upgrading to Dapper 6.06 I simply inserted mine 1GB JetFlash into USB port and there was a window with contents of a disk.

After upgrading

```
$ lsmod |grep usb
usbhid                 35264  0
usbcore               118044  4 usbhid,ehci_hcd,uhci_hcd
```

Plug the JetFlash:
```
$ tail -f /var/log/messages
Jun 22 12:02:29 localhost kernel: [4294890.446000] usb 4-3: new high speed USB device using ehci_hcd and address 3

```
and that's all!

I have added "*usb_storage*" to /etc/modoles

Plug the JetFlash:

```
$ tail -f /var/log/messages
Jun 22 10:31:01 localhost kernel: [4295005.628000] usb 4-3: new high speed USB device using ehci_hcd and address 3
Jun 22 10:31:01 localhost kernel: [4295005.778000] scsi0 : SCSI emulation for USB Mass Storage devices
Jun 22 10:31:06 localhost kernel: [4295010.779000]   Vendor: JetFlash  Model: TS1GJF2A/120      Rev: 8.07
Jun 22 10:31:06 localhost kernel: [4295010.779000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Jun 22 10:33:18 localhost kernel: [4295141.975000] SCSI device sda: 2047998 512-byte hdwr sectors (1049 MB)
Jun 22 10:33:18 localhost kernel: [4295141.976000] sda: Write Protect is off
Jun 22 10:33:18 localhost kernel: [4295141.978000] SCSI device sda: 2047998 512-byte hdwr sectors (1049 MB)
Jun 22 10:33:18 localhost kernel: [4295141.980000] sda: Write Protect is off
Jun 22 10:33:18 localhost kernel: [4295141.980000]  /dev/scsi/host0/bus0/target0/lun0: unknown partition table
Jun 22 10:33:18 localhost kernel: [4295141.982000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
```

But there no window with contents of a disk and no automount! Yes, I can mount /dev/sda manually, but ...

By the way when I have inserted the CD/DVD there no "window" too, but automounting (/media/cdrom) has worked

System --> Preferences --> Removable media, options for automount are checked.

**The question is how can I solve these inconveniences?**

brg,
Serhiy.

---

### Post by timetunnel on 2006-06-22
There seem to be problems with the latest kernel 2.6.15-25 in Dapper (mouse, keyboard, performance and/or USB stuff):

[http://www.ubuntuforums.org/showthread.php?t=197484](http://www.ubuntuforums.org/showthread.php?t=197484)

I'm not sure if that's your problem actually. But maybe this helps: if you really have this latest kernel installed, install the former kernel 2.6.15-23 as well. When rebooting, choose this one from the list in the bootmanager and see what happens. I didn't have problems with USB but others, and booting to 2.6.15-23 instead of 2.6.15-25 solved some problems for me.

---

### Post by gray380 on 2006-06-22
Thanx, but I have older version of kerner:

$ uname -r
2.6.12-10-686

[QUOTE=timetunnel]There seem to be problems with the latest kernel 2.6.15-25 in Dapper (mouse, keyboard, performance and/or USB stuff):

[http://www.ubuntuforums.org/showthread.php?t=197484](http://www.ubuntuforums.org/showthread.php?t=197484)

I'm not sure if that's your problem actually. But maybe this helps: if you really have this latest kernel installed, install the former kernel 2.6.15-23 as well. When rebooting, choose this one from the list in the bootmanager and see what happens. I didn't have problems with USB but others, and booting to 2.6.15-23 instead of 2.6.15-25 solved some problems for me.[/QUOTE]

---

### Post by rcarring on 2006-06-22
You have a Breezy kernel not Dapper. I found that when I tried doing a dist-upgrade my kernel wasn't upgraded.

---

### Post by gray380 on 2006-06-22
Ridiculously, I have gone to install a new kernel.
Thankx a lot.

[QUOTE=rcarring]You have a Breezy kernel not Dapper. I found that when I tried doing a dist-upgrade my kernel wasn't upgraded.[/QUOTE]

---

### Post by gray380 on 2006-06-22
The problem was solved after installation of the correct version of a kernel. 
Why it was not updated by the Updte-manager while upgrading? (rhetorical question)

---

