---
title: "Ubuntu x64 - Jmicron RAID 0"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Prigity on 2008-01-18
Hey guys,

I'm having a bit of trouble getting this all set up

Rig specs :
Core2Duo E6320 @ 3ghz
GIGABYTE GA-965P-DS3 Rev. 3.3, Current BIOS
1x1gb DDR2 800
2x80gb Maxtor drives (RAID0)
1x250gb Seagate (not on the Jmicron controller)
Radeon x1300 (Sapphire fan less edition)

So, I can boot off the disk and everything, but when I get to the partition segment of the install, my 2 80gb drives just show up and not my RAID array...I've been trying to figure this out all night

This is how I've got my partitions set up:

RAID
1x 130gb - Windows
1x20gb - Awaiting Ubuntu

Non RAID
1x250gb - Storage

I've learned all about how this controller just sets up what is known as FAKEraid, and I've read up a bit about it, but I still can't get it to work right.

I've checked off "universe" in "Software Resources"
Installed the "DMRAID" in the Synaptic Package Manager
And I've done the terminal command "sudo dmraid -ay

Now, it gives me an error here 

```
ubuntu@ubuntu:~$ sudo dmraid -ay
/dev/sdb: "nvidia" and "jmicron" formats discovered (using jmicron)!
RAID set "jmicron_OMGFAST         " already active
RAID set "nvidia_cbeffbbg" already active
ERROR: dos: partition address past end of RAID device
ubuntu@ubuntu:~$
```

I'm guessing that's the culprit right there, but I have no idea what this means (I'm no Linux expert.....yet ;-)  )

Even though it got an error, I tried the installer again, but the same results as before - my 3 drives just show up independently.

If any of you guys could shed some light on this, it would be greatly appreciated, as I'd like to get back into Linux

P.S. If I didn't make this clear higher up, this is going to be a dual boot of Windows VISTA and Ubuntu 7.1 x64.
I would rather not have to break the RAID and reinstall, but I am willing to if I have to.

---

### Post by Prigity on 2008-01-19
Anyone have any ideas?

---

