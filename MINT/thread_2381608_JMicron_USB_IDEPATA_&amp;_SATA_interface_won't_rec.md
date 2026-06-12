---
title: "JMicron USB IDE/PATA &amp; SATA interface won't recognize SATA drives (IDE drives work)"
date: 2018-01-02
forum: MINT
---

### Post by scragnoth on 2018-01-02
Hi, this is my first post in this forum and I hope you can help me with my problem.

I just got a "HAMA AA25" USB to IDE/PATA & SATA combo interface and wanted to use it with my Linux Mint installation:

```

Release Linux Mint 17.2 Rafaela 64-bit
Kernel Linux 3.16.0-38-generic x86_64
MATE 1.10.2
```

The device recognizes itself as

```

JMicron USB to ATA/ATAPI Bridge (0100)
Serial Number 152D203380B6
```

Problem: IDE drives work fine with it, no complaint there. I have another interface for IDE only which also works fine, and another one for SATA only (USB 3.0 compatible) which works fine as well. What doesn't work with the JMicron device are SATA drives.
Maybe I see where the problem is: My system recognizes the device as just an "ATA/ATAPI Bridge" and doesn't "see" that it supports SATA drives also.

I read in the following thread about a workaround which I cannot get to work unfortunately (and I wasn't able to re-use the thread for my problem since it is closed now): [https://ubuntuforums.org/showthread.php?t=966321&page=2](https://ubuntuforums.org/showthread.php?t=966321&page=2)

> 
_[COLOR=#000000]drave40 wrote:[/COLOR]_

[COLOR=#000000]Just in case anyone still has this problem ( I did, that's how i landed here)[/COLOR]

[COLOR=#000000]disconnect from USB[/COLOR]
[COLOR=#000000]find jmicron driver. on my system it's called "pata_jmicron"[/COLOR]
[COLOR=#000000]load it, "modprobe pata_jmicron"[/COLOR]
[COLOR=#000000]connect to USB gain[/COLOR]

[COLOR=#000000]dahdah everything is visible. well, it is here[/COLOR]

[COLOR=#000000]cheers[/COLOR]

If I type

```

modprobe pata_jmicron
```

into my terminal I get

```

modprobe: ERROR: could not insert 'pata_jmicron': Operation not permitted
```

I can rule out any problems caused by faulty drives or their partitions, and also those caused by a faulty power supply.

---

### Post by DuckHook on 2018-01-02
*Thread moved to **MINT** as the more appropriate forum.*

---

### Post by sudodus on 2018-01-03
I am afraid that the device is not fully compatible (at least not with the version of Mint, that you are using), that no linux drive for the SATA connection is found for your JMicron USB IDE/PATA & SATA interface. Maybe it works with some version of Ubuntu.

I have a corresponding device (USB 2.0 to IDE & SATA), that is made in China, without any particular brand name, simply called "EASY-IDE/SATA". It is several years old and it works with both IDE and SATA, both for connecting a data drive and for booting.

I guess you need some luck to get an adapter where everything works, particularly for booting. Anyway, I'm glad your adapter works for IDE drives, because it is easy nowadays to find SATA-only adapters, but not so easy to find IDE adapters.

---

### Post by oldfred on 2018-01-03
We have seen other posts where some adapters just do not work with gpt partitioned drives (regardless of size), do not work with multi-TB sized drives, do not work on USB3 ports or some USB ports (so also motherboard issue).

Best to be sure your adapter works with your configuration, but many do not post detailed specs.

---

### Post by scragnoth on 2018-01-03
Thank you, seems tricky, maybe it's not worth the effort in the end since I have another adapter for SATA already which works fine. Just would have been nice to be able to transfer data directly between my SATA drives.

The SATA drive spins up as expected but won't show up in the Disk utility, just the adapter itself is shown. I tried directly on USB 2.0 port and with a passive Hub in between. Both worked fine when I used it with IDE drives. I powered the IDE drives with an external brick which has a molex connector on the other end. It is rated 5V / 12V with 1,5 A for both lines. For SATA-usage I need to put the molex directly into the adapter itself, there it gets routed to the power pins on the SATA drive.

All drives are NTFS since I want cross-compatibility between Linux and Windows. I don't want to directly boot from them through the adapter.

---

