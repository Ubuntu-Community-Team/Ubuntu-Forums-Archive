---
title: "&quot;Failed to delete multidisk device&quot;"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by rkillcrazy on 2007-11-23
Hello, again...

I've been playing around with software RAID and am testing a few things.  When I go to reload, I wish to delete the partitions and start again from scratch.  I use the ALTERNATE installer disk and everything looks fine until I go to set up the RAID again.  I then try to delete the RAID volume (md0) but it gives the following error:
```

[CENTER]
Failed to delete multidisk device
There was an error deleting the multidisk device.  It may be in use.
[/CENTER]
```

I'm curious as to how it's still in use when there are no partitions left on it and I had just booted up with the install disk.  Note, before going in to set up the RAID partitions, there's no option to configure the RAID device, which is where one can delete the multidisk devices, so I don't know how I can delete this thing before this point in the install.

I have gotten it done in some roundabout way by erasing the data on the partition(s) before deleting them but that takes 30-45 minutes per disk!  There has to be a better way!

11-23-07
1610 EST

---

### Post by Pumalite on 2007-11-23
If you are going to use Raid; read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by rkillcrazy on 2007-11-23
> **Pumalite said:**
> If you are going to use Raid; read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Is the built-in software RAID that busted!?  I've been playing with it for some time and I just figured I was doing something wrong when it came time to reinstall.

I've seen this page before and I'll give it another shot.  I think something bad happened last time but I can't recall what...

11-23-07
1635 EST

---

### Post by Pumalite on 2007-11-23
In my opinion, if you are not using hardware Raid, don't waste your time.

---

### Post by siouzi on 2007-11-24
I managed to finally solve this extremely annoying problem which I had also trouble with. Basically you have to stop the existing md devices and then wipe them out using the shell. So, execute a shell and use

```
mdadm --stop /dev/mdX
mdadm --zero-superblock /dev/sdX
```

See [* this source *]("http://ubuntuforums.org/showthread.php?p=2459683") for more detailed information!

---

