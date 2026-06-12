---
title: "hdd: command error: status=0x51 { DriveReady SeekComplete Error }"
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by yccheok on 2005-05-25
Just very recently after few months usage, I discover recently my ubuntu have the following boot error message, which seem critical to me  ](*,)  ](*,)  ](*,) 

I do a quick check on /var/log/messages

[I]May 26 03:54:31 localhost kernel: eth0: network connection up using port A
May 26 03:54:31 localhost kernel:     speed:           100
May 26 03:54:31 localhost kernel:     autonegotiation: yes
May 26 03:54:31 localhost kernel:     duplex mode:     full
May 26 03:54:31 localhost kernel:     flowctrl:        symmetric
May 26 03:54:31 localhost kernel:     irq moderation:  disabled
May 26 03:54:31 localhost kernel:     scatter-gather:  enabled
May 26 03:54:31 localhost kernel:     tx-checksum:     enabled
May 26 03:54:31 localhost kernel:     rx-checksum:     enabled
May 26 03:54:31 localhost kernel: NET: Registered protocol family 10
May 26 03:54:31 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
May 26 03:54:31 localhost kernel: IPv6 over IPv4 tunneling driver
May 26 03:54:31 localhost kernel: ACPI: Power Button (FF) [PWRF]
May 26 03:54:33 localhost kernel: hdd: command error: status=0x51 { DriveReady SeekComplete Error }
May 26 03:54:33 localhost kernel: hdd: command error: error=0x54
May 26 03:54:33 localhost kernel: end_request: I/O error, dev hdd, sector 0
May 26 03:54:33 localhost kernel: hdd: command error: status=0x51 { DriveReady SeekComplete Error }
May 26 03:54:33 localhost kernel: hdd: command error: error=0x54
May 26 03:54:33 localhost kernel: end_request: I/O error, dev hdd, sector 8
May 26 03:54:33 localhost kernel: hdd: command error: status=0x51 { DriveReady SeekComplete Error }
May 26 03:54:33 localhost kernel: hdd: command error: error=0x54
May 26 03:54:33 localhost kernel: end_request: I/O error, dev hdd, sector 16
May 26 03:54:33 localhost kernel: hdd: command error: status=0x51 { DriveReady SeekComplete Error }

......................(Lot more to go)

May 26 03:54:33 localhost kernel: hdd: command error: status=0x51 { DriveReady SeekComplete Error }
May 26 03:54:33 localhost kernel: hdd: command error: error=0x54
May 26 03:54:33 localhost kernel: end_request: I/O error, dev hdd, sector 512
May 26 03:54:37 localhost kernel: NVRM: not using NVAGP, AGPGART is loaded!!
May 26 03:54:38 localhost kernel: NVRM: not using NVAGP, AGPGART is loaded!!
May 26 03:55:01 localhost gconfd (yccheok-3762): starting (version 2.8.1), pid 3762 user 'yccheok'[/I]

Can anyone please advice me on this? Where I should start to tackle the problem?

Thanks!

cheok

---

### Post by jdong on 2005-05-25
Is hdd a hard drive or CD-ROM? This message generally indicates either physical defects with your drive, or insane hdparm settings. If you've never played with hdparm before, rule out the latter.


If hdd is a CD-ROM drive, it just means the disc inserted at the time had scratches or was otherwise unreadable.

Otherwise, I recommend backing up important data, and doing a detailed badblocks search. Boot into Single User (sudo init S, or Recovery Mode @ startup menu), then run "fsck -c /dev/hdd". This is like ScanDisk's surface scan, and may take more than an hour to complete, during which time you can't use this computer.

---

### Post by yccheok on 2005-05-26
[QUOTE=jdong]Is hdd a hard drive or CD-ROM? This message generally indicates either physical defects with your drive, or insane hdparm settings. If you've never played with hdparm before, rule out the latter.


If hdd is a CD-ROM drive, it just means the disc inserted at the time had scratches or was otherwise unreadable.

Otherwise, I recommend backing up important data, and doing a detailed badblocks search. Boot into Single User (sudo init S, or Recovery Mode @ startup menu), then run "fsck -c /dev/hdd". This is like ScanDisk's surface scan, and may take more than an hour to complete, during which time you can't use this computer.[/QUOTE]
 Sorry guy, I realize that an audio CD is in my CD-ROM that time. After I remove that audio CD and restart, problem gone :)

Thanks for help!

---

