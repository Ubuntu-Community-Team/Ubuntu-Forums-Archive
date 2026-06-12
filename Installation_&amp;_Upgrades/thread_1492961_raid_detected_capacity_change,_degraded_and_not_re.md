---
title: "raid detected capacity change, degraded and not rebuilding"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Anck on 2010-05-25
Hi all,

I set up a system using the alternate installer. I have two identical disks, with 4 partitions each. They form 4 raid1 arrays. /dev/sda4 and /dev/sdb4 make up /dev/md3, and that serves as a physical volume for LVM, which holds /usr, /usr/local/, /var, /tmp and /home. After installation, I let the arrays synchronize completely. All was well. Then I had to reboot, because I wanted to turn on data=journal for all partitions including /. When the system came back up, /dev/md3 was marked degraded. I opened disk utility and selected "check array". This started a rebuild. About 1/3rd of the way, the rebuild stopped, and the array is listed as degraded and idle. I tried again, same thing happened.

Excerpt from my /var/log/messages:

```

May 25 13:54:23 quad kernel: [    6.054045] raid1: raid set md3 active with 1 out of 2 mirrors
May 25 13:54:23 quad kernel: [    6.054059] md3: detected capacity change from 0 to 1493789769728
May 25 13:54:23 quad kernel: [    6.054809]  md3: unknown partition table

``````

May 25 15:00:22 quad kernel: [ 3970.353831] md: requested-resync of RAID array md3
May 25 15:00:22 quad kernel: [ 3970.353833] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
May 25 15:00:22 quad kernel: [ 3970.353836] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for requested-resync.
May 25 15:00:22 quad kernel: [ 3970.353840] md: using 128k window, over a total of 1458779072 blocks.
May 25 16:02:08 quad pulseaudio[1935]: ratelimit.c: 567 events suppressed
May 25 16:02:38 quad kernel: [ 7706.981712] ata2: hard resetting link
May 25 16:02:39 quad kernel: [ 7707.512515] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 25 16:02:39 quad kernel: [ 7707.515541] ata2.00: configured for UDMA/133
May 25 16:02:39 quad kernel: [ 7707.515545] ata2.00: device reported invalid CHS sector 0
May 25 16:02:39 quad kernel: [ 7707.515552] ata2: EH complete
May 25 16:02:39 quad kernel: [ 7707.525995] md: super_written gets error=-5, uptodate=0
May 25 16:02:39 quad kernel: [ 7707.553343] md: md3: requested-resync done.
May 25 16:02:40 quad kernel: [ 7708.367816] RAID1 conf printout:
May 25 16:02:40 quad kernel: [ 7708.367820]  --- wd:1 rd:2
May 25 16:02:40 quad kernel: [ 7708.367823]  disk 0, wo:1, o:1, dev:sda4
May 25 16:02:40 quad kernel: [ 7708.367825]  disk 1, wo:0, o:1, dev:sdb4
May 25 16:02:40 quad kernel: [ 7708.367826] RAID1 conf printout:
May 25 16:02:40 quad kernel: [ 7708.367827]  --- wd:1 rd:2
May 25 16:02:40 quad kernel: [ 7708.367829]  disk 0, wo:1, o:1, dev:sda4
May 25 16:02:40 quad kernel: [ 7708.367831]  disk 1, wo:0, o:1, dev:sdb4

```The blocks of RAID1 conf printout are repeated over and over and over. SMART says there is nothing wrong with the disks. Why is my raid array not rebuilding? How do I fix it? "hard resetting link" doesn't sound good, and would likely cause the rebuild to fail, but I don't know what could be causing it..?

/proc/mdstat after the second rebuild attempt failed (and my log started filling up with RAID1 conf spam again):

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5]  [raid4] [raid10] 
md2 : active raid1 sdb3[1] sda3[0]
      1952704 blocks [2/2] [UU]
      
md1 : active raid1 sdb2[1] sda2[0]
      3906496 blocks [2/2] [UU]
      
md3 : active raid1 sda4[2] sdb4[1]
      1458779072 blocks [2/1] [_U]
      
md0 : active raid1 sda1[0] sdb1[1]
      498624 blocks [2/2] [UU]
      
unused devices: <none>

```

---

### Post by Anck on 2010-05-25
I don't know if it matters, but I also found this in the logs for both sda and sdb:

```
May 22 23:58:39 quad kernel: [    2.450021] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 22 23:58:39 quad kernel: [    2.451344] ata2.00: ATA-8: ST31500341AS, SD17, max UDMA/133
May 22 23:58:39 quad kernel: [    2.451346] ata2.00: 2930277168 sectors, multi 0: LBA48 NCQ (not used)
May 22 23:58:39 quad kernel: [    2.451353] ata2.00: WARNING: device requires firmware update to be fully functional.
May 22 23:58:39 quad kernel: [    2.451354] ata2.00:          contact the vendor or visit http://ata.wiki.kernel.org.
May 22 23:58:39 quad kernel: [    2.453048] ata2.00: configured for UDMA/133
```Could a firmware update help, or would that just be asking for more trouble?

---

### Post by Anck on 2010-05-26
Well I downloaded the seagate update utility for my disks, tried it and of course it came back saying my disk is fine and does not need a firmware update, then flat out refused to do one. So much for that option..
 
I tried rebuilding the raid again over night as well, according to /proc/mdstat it rebuilt completely and then dropped straight back to degraded mode. :(

---

### Post by Anck on 2010-05-26
Seems to have been a hardware / firmware issue (seagate 7200.11 w/ SD17 firmware); replaced both disks and the raid array no longer fails. Marking this resolved.

---

