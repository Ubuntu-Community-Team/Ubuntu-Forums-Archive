---
title: "How to Backup Current Ubuntu to another HDD?"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by cci[RR]us on 2011-05-04
Hi,

I am going to dist-upgrade my 10.10 installation to 11.04, but as precaution, I would like to replicate my existing installation onto another hard disk and perform the dist-upgrade there.

When I am in booted into my current 10.10 installation, the hard disk (MBR, 4GB) is partitioned as such:

[INDENT]/dev/sda1 - /boot
/dev/sda2 - swap
/dev/sda3 - /[/INDENT]

I have an empty hard disk (MBR, 10GB) connected to the PC, and I partitioned to have a similar layout.

[INDENT]/dev/sdb1 - /boot
/dev/sdb2 - swap
/dev/sdb3 - /[/INDENT]

Since the 2 HDDs are of different sizes, I made /dev/sdb3 larger.


*_My question is:_ what is the easiest way to create a backup of my current working Ubuntu onto my secondary hard disk?*


I hope to perform the backup while booted into my existing 10.10 system; or I have no other choices but to boot from a LiveCD (e.g. Clonezilla) for backup?

Thank you!

---

### Post by mörgæs on 2011-05-04
It is good that you are careful, but the best you can do is a fresh install of 11.04 on the small hard drive. 

Don't do dist-upgrades, not even with a backup at hand.

---

### Post by Gas Addict on 2011-05-04
I'm looking to do the same thing but with a twist. I am trying to copy my current Ubuntu 11.04 install (which is on a 10GB partition) to my 16GB USB flash drive. 

The Ubuntu is on /dev/sda5 and the USB flash drive is /dev/sdb1.

When I use dd to backup the Ubuntu install to the USB flash drive it works, but I am unable to boot from it.

This is the command I'm using

```
dd if=/dev/sda5 of=/dev/sdb1 bs=1024
```

Could anyone help me get it to boot?  Thank you.

---

### Post by cci[RR]us on 2011-05-04
> **mörgæs said:**
> 
Don't do dist-upgrades, not even with a backup at hand.

What could possibly go wrong even if I have my backup? At the worst, I'll just bork one copy and the backup still remains healthy and usable. That is precisely the point of the backup.

---

### Post by mörgæs on 2011-05-04
Nothing goes wrong with regards to data loss, but the process is long and risky compared to a fresh install. 

You will get the best impression of 11.04 when installed from scratch.

---

### Post by cci[RR]us on 2011-05-04
I had been doing that - fresh installations instead of dist upgrades - since Hardy, and I wish to try something different. Think of it as a learning experience, rather than for practical purposes.

So on this note, let's get back to the topic. Any ideas from the rest?

---

### Post by Gas Addict on 2011-05-04
I'm not sure if you can be logged into your system while you're backing up unless you use something that copies files instead of actually does a low-level system backup of every byte on the drive. 

I would use the dd command from a liveUSB or liveCD. It's really easy to use.

dd if=source partition of=target partition bs=1024 

if stands for input file and you can make it /dev/sda1 and your target would be /dev/sdb1 .  You could just do that for all three of your partitions and you would have an exact copy of your current setup on your second drive.

---

