---
title: "All was well. Added a new drive. Now can't boot"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by savvyside on 2006-08-01
Hello.

I am a Ubuntu lover, from Hoary days. This is my 3rd box. It is a high end system (4400GHz, 2G ram, etc). I have been very happy with Dapper Drake. No problems. 

I had two drives that I partitioned at install. The first disk (Raptor 74G) is my boot disk and is in the first sata slot, sda, and the other disk (260G) is for data and is in the second sata slot and is seen as sdb.

At this point, all was well...

Then, I added an additional 300G drive in the 3rd sata slot. System would not boot. I used a dapper live/install CD to boot up. I saw the new drive, but now IT was seen as sda!!! I went ahead and formatted it (successfully) (as EXT3). I reboot, but it will not start up (it stops at mounting filesystem).


Bottom line: Adding a new drive in the 3rd sata slot of motherboard is now seen as SDA and since it is blank, I can't boot. 

What is wrong? Any ideas?

thanks!

michael
If i pull the new drive, everything boots fine.

---

### Post by mlind on 2006-08-02
That's probably grub getting confused of changed drive ordering. You should boot with livecd and reinstall grub back to same partition where it currently lies.

```

sudo grub-install /dev/xxx

```

Where /dev/xxx is a device (/dev/hda, /dev/sda, etc..), **not** a filesystem!

---

