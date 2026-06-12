---
title: "Raid Formatting during install V12.04 Server 32 bit."
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by tltemple on 2012-05-18
I am installing V12.04 Server, 32 bit on a system with 4 hard drives.  2x160GB, 2X1TB.

I partitioned the 2 160GB drives and formed Raid1's, and installed the OS on those drives.

After installing the OS, I am manually adding the 1TB drives as a raid1.  I partitioned them (1 partition, whole drive), then set them as raid 1, and am formatting the raid drive right now.

I am getting errors during this process, and the progress is very slow.  It has been running for over 12 hours.  It is nearing completion, but I am not sure whether to suspect that I have hardware problems.

Here are some of the errors:


May 18 07:58:32 LxEngServer2 kernel: [59978.714661] ata5.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
May 18 07:58:32 LxEngServer2 kernel: [59978.716083] ata5.00: irq_stat 0x40000008
May 18 07:58:32 LxEngServer2 kernel: [59978.717592] ata5.00: failed command: READ FPDMA QUEUED
May 18 07:58:32 LxEngServer2 kernel: [59978.718916] ata5.00: cmd 60/80:00:00:6a:3e/00:00:01:00:00/40 tag 0 ncq 65536 in
May 18 07:58:32 LxEngServer2 kernel: [59978.718918]          res 41/40:00:14:6a:3e/00:00:01:00:00/40 Emask 0x409 (media error) <F>
May 18 07:58:32 LxEngServer2 kernel: [59978.721615] ata5.00: status: { DRDY ERR }
May 18 07:58:32 LxEngServer2 kernel: [59978.723123] ata5.00: error: { UNC }
May 18 07:58:32 LxEngServer2 kernel: [59978.729325] ata5.00: configured for UDMA/133
May 18 07:58:32 LxEngServer2 kernel: [59978.729340] ata5: EH complete
May 18 07:59:25 LxEngServer2 kernel: [60031.629516] ata5.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
May 18 07:59:25 LxEngServer2 kernel: [60031.630885] ata5.00: irq_stat 0x40000008
May 18 07:59:25 LxEngServer2 kernel: [60031.632223] ata5.00: failed command: READ FPDMA QUEUED
May 18 07:59:25 LxEngServer2 kernel: [60031.633766] ata5.00: cmd 60/80:00:80:78:3e/00:00:01:00:00/40 tag 0 ncq 65536 in
May 18 07:59:25 LxEngServer2 kernel: [60031.633769]          res 41/40:00:ce:78:3e/00:00:01:00:00/40 Emask 0x409 (media error) <F>
May 18 07:59:25 LxEngServer2 kernel: [60031.636459] ata5.00: status: { DRDY ERR }
May 18 07:59:25 LxEngServer2 kernel: [60031.637928] ata5.00: error: { UNC }
May 18 07:59:25 LxEngServer2 kernel: [60031.644099] ata5.00: configured for UDMA/133
May 18 07:59:25 LxEngServer2 kernel: [60031.644114] ata5: EH complete
May 18 08:01:41 LxEngServer2 avahi-daemon[825]: Invalid query packet.
May 18 08:02:25 LxEngServer2 avahi-daemon[825]: last message repeated 2 times
May 18 08:02:25 LxEngServer2 kernel: [60211.248293] ata5.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
May 18 08:02:25 LxEngServer2 kernel: [60211.249660] ata5.00: irq_stat 0x40000008
May 18 08:02:25 LxEngServer2 kernel: [60211.250982] ata5.00: failed command: READ FPDMA QUEUED
May 18 08:02:25 LxEngServer2 kernel: [60211.252375] ata5.00: cmd 60/80:00:80:a8:3e/00:00:01:00:00/40 tag 0 ncq 65536 in
May 18 08:02:25 LxEngServer2 kernel: [60211.252381]          res 41/40:00:84:a8:3e/00:00:01:00:00/40 Emask 0x409 (media error) <F>
May 18 08:02:25 LxEngServer2 kernel: [60211.255375] ata5.00: status: { DRDY ERR }
May 18 08:02:25 LxEngServer2 kernel: [60211.256760] ata5.00: error: { UNC }
May 18 08:02:25 LxEngServer2 kernel: [60211.263044] ata5.00: configured for UDMA/133
May 18 08:02:25 LxEngServer2 kernel: [60211.263059] ata5: EH complete
May 18 08:02:27 LxEngServer2 kernel: [60213.356578] ata5.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
May 18 08:02:27 LxEngServer2 kernel: [60213.357949] ata5.00: irq_stat 0x40000008
May 18 08:02:27 LxEngServer2 kernel: [60213.359261] ata5.00: failed command: READ FPDMA QUEUED
May 18 08:02:27 LxEngServer2 kernel: [60213.360650] ata5.00: cmd 60/80:00:80:a8:3e/00:00:01:00:00/40 tag 0 ncq 65536 in
May 18 08:02:27 LxEngServer2 kernel: [60213.360655]          res 41/40:00:fe:a8:3e/00:00:01:00:00/40 Emask 0x409 (media error) <F>
May 18 08:02:27 LxEngServer2 kernel: [60213.363613] ata5.00: status: { DRDY ERR }
May 18 08:02:27 LxEngServer2 kernel: [60213.364961] ata5.00: error: { UNC }
May 18 08:02:27 LxEngServer2 kernel: [60213.371220] ata5.00: configured for UDMA/133
May 18 08:02:27 LxEngServer2 kernel: [60213.371235] ata5: EH complete
May 18 08:04:16 LxEngServer2 avahi-daemon[825]: Invalid query packet.
May 18 08:05:28 LxEngServer2 avahi-daemon[825]: last message repeated 5 times




My questions are:

1) Should I trust the drive(s), even if the process finishes and appears to function?

2) Does this process (format 1TB raid) typically take anywhere near this long? (the 160GB drives raided and formatted in less than a couple of minutes, probably).

Thanks

---

### Post by jadtech on 2012-05-18
I don't think it should take that long but I am not sure,  it looks as if the drive is reporting bad areas on the disk it cant read from this cant be a good thing ..

I have any experance with this just  know it cant be all good

---

### Post by tltemple on 2012-06-06
It seems that one hard drive in the mix was bad (new, but bad).  The formatting process only takes a few minutes at most when the drives are good.

---

