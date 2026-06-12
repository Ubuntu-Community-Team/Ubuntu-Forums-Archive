---
title: "Partitions problem - lost 250 mb"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by loopinaloop on 2012-10-21
I was using KDE Partition Manager and while resizing was in process, my computer has turned off. Now, I have installed Ubuntu 12.10 with option of removing anything else and installing only Ubuntu. Even then, I have something like 250 MB allocated to unused partition that cannot be formated or merged with my primary one. Installation should do the trick but it didn't.

Maybe I can use LVM to do this but I haven't ever used it. Is there a way to completely wipe clean my hard drive that I'm not aware of? Please, help me out. I'm a DJ and artist and I need all space available. Nowadays 500 GB isn't much.

---

### Post by Bucky Ball on 2012-10-21
And 250Mb is much less. You will find this probably being used by the system for some reason. Perhaps to keep the next partition's beginning sector in the correct place, creating correct sized blocks and readable.

It is not unusual to discover these 'random' bits. You could be there awhile trying to kill it but I'll be interested to see your resolution ... ;)

PS: If you're a working DJ perhaps put some money away from the next few gigs and grab an external drive or two ... eSATA or Firewire best for what you do (USB 3 also but know nothing about that). You're right: 500Gb isn't much. If you use your machine for recording, etc, you should be running the software from one drive and recording to another anyhow for better latency, among other things. Generally rule of thumb ...

---

### Post by funicorn on 2012-10-22
sudo sfdisk -dx

---

### Post by loopinaloop on 2012-10-22
[QUOTE=sudo sfdisk -dx]Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=     2048, size=976769024, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0

/dev/sda5 : start=   501760, size=976269312, Id=8e
    -     : start=     2048, size=        0, Id= 0
    -     : start=     2048, size=        0, Id= 0
    -     : start=     2048, size=        0, Id= 0


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/mapper/ubuntu-root: unrecognized partition table type
No partitions found

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/mapper/ubuntu-swap_1: unrecognized partition table type
No partitions found
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       32, size= 31277024, Id= c, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
[/QUOTE]
Normally, everything should be allocated to sda1. How to fix it?

---

### Post by darkod on 2012-10-22
There is no better way to get rid of everything than writing new blank partition table. If you do want to start freash on /dev/sda for example, simply boot the cd in live mode and in terminal do:
```
sudo parted /dev/sda
mklabel msdos
exit
```

That should do it. After that you can install.

There seems to be LVM on /dev/sdb, are you using that?

---

### Post by buckyaustin on 2012-10-22
If you want to manage space you could use bleachbit. It will remove alot of the unnecessary files from your computer thus giving you more space to use. I'm sure that would make up for the 250MB space you have lost.

---

### Post by loopinaloop on 2012-10-23
> **darkod said:**
> There is no better way to get rid of everything than writing new blank partition table.
Sounds like what I want to do. But after the 'mklabel msdos' command I get the following error:
> Error: Partition(s) 5 on /dev/sda have been written, but we have been unable to
inform the kernel of the change, probably because it/they are in use.  As a
result, the old partition(s) will remain in use.  You should reboot now before
making further changes.
Ignore/Cancel?How to resolve this?

EDIT: Oh, and aside from sda5, my drive is empty.

---

### Post by darkod on 2012-10-23
Just say Ignore, exit the parted prompt and reboot. It seems one of the partition was mounted, maybe the swap because it gets mounted in live mode, so that message says the change will be delayed until you reboot.

If I understand it correctly, after a reboot the disk will show as empty, new partition table.

---

### Post by loopinaloop on 2012-10-23
Sure, it's wiped and clean but I've lost 34.24 GB! GB!!!

Now, with GParted I see no other unallocated space, no sda5, nothing. Just 465.76 GB of unallocated space out of original 500.01 GB.

What happened? What can I do?

---

### Post by darkod on 2012-10-23
Calm down. Gparted shows you GiB, not GB.

A disk of 500GB never has true 500GiB because disk manufacturers use the decimal system, not the binary.

For disk manufacturers 1GB is 1 billion bytes.

In binary system 1GiB is 1024x1024x1024 bytes.

That is the difference.

---

