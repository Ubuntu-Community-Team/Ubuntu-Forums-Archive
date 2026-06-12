---
title: "GParted error"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by agim on 2008-02-10
I am trying to resize a drive to dual boot with XP for a friend. I started the GParted cd and got an error that looked like this.

hda: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hda: task_in_intr: error=0x40 { UncorrectableError }, LBAsec=128203481, high=7, low=10762969, sector=128203478
ide: failed opcode was unknown
end_request: I/O error on dev hda, sector 128203481
Buffer I/O error on device hda2 logical block 128107091

I googled this and all I could find was that this sometimes happens with older drives.

1)Does anybody have any experience with this?
2)Is this the case? Just and old drive?
3)Either way, what are my options/solutions?

Thanks

---

### Post by Pumalite on 2008-02-10
Check your drive with TestDisk and/or rescuecd (google them)
Post your specs.

---

### Post by agim on 2008-02-10
Thanks for the quick reply. Unfortunately, the XP computer is not mine, its a friends. I will post this when I get a chance.

I know it may be impossible to tell, but does this type of error tell you anything useful in and of itself?

---

### Post by mrsteveman1 on 2008-02-10
It likely means the drive found an error it was unable to correct on its own. Normally when a drive reads data it can tell if the data was read incorrectly by doing an ECC check, sometimes the ECC check fails.

The drive may still be usable but i wouldn't trust it anymore. If it has important data on it there are ways to get it off, if not buy a new disk.

---

### Post by agim on 2008-02-11
Everywhere I read, people say that this is a major problem. But Windows still boots and works just fine. No problem whatsoever. Only 7.84 MB was partitioned before GParted stopped, and XP didn't even seem to notice it was gone.

But as far as not being able to get data off of the drive, thats just not happening.

---

