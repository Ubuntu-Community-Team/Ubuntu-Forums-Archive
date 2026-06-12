---
title: "Two drives, two Ubuntu installs. How to remove one?"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by pognonec on 2009-12-22
Description of the situation:

I have a recent Dell PC with two HD.
One with Windows Vista (it came that way)
One with Ubuntu (I installed it, and it worked fine: that is the one I use)

I got a "free" upgrade for Vista to W7. I stupidly used it, and of course it screwed up my boot. Could not boot 9.10 any more, and could not succeed to reinstall grub2.

So I reinstalled (a second) Ubuntu 9.10 on my first drive, completely wiping out windows :)
And magic, I could change the (new) grub2 menu (from the second Ubuntu install, on the first drive) to boot on my original Ubuntu 9.10 install (on the second drive), where all my stuff is.


My question:

how can I remove the last Ubuntu install (on the first drive), without destroying my booting to my second drive?

Please make it as simple as possible ;)

---

### Post by Grenage on 2009-12-22
You're in luck, it's nice and easy.  First remove the option from the Grub2 menu (option 7 in this link):

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Then make sure you can boot up, and wipe the old partition using gparted.

---

### Post by audiomick on 2009-12-22
> **Grenage said:**
> You're in luck, it's nice and easy.  First remove the option from the Grub2 menu (option 7 in this link):

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Then make sure you can boot up, and wipe the old partition using gparted.

Take the opportunity to save all the stuff you want to keep out of your old install to the new one before you wipe it! :)

---

### Post by pognonec on 2009-12-22
> **Grenage said:**
> First remove the option from the Grub2 menu
Then make sure you can boot up, and wipe the old partition using gparted.

Great! That sounds simple enough indeed. 
But just to make sure I won't bury myself deeper: the "old" partition I want to remove is actually the newest one, from the second install of Ubuntu that saved my butt, on the first HD. Won't wiping it also remove grub, which I guess is located in it (like /boot/grub), rendering boot impossible again??
I know, I could simply try, but...

---

### Post by Grenage on 2009-12-22
Yes, that is true.  What you can do is after wiping the partition, boot using your ubuntu live CD (normal install disc).  You can then mount the drive and reinstall grub.  My grub is really rusty, but I think it should be somewhere along the lines of:

```
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
sudo grub-install --root-directory=/mnt/sda1 sda
```

Assuming sda1 is the drive and partition of your first ubuntu install.  Doubt-check the commands with a quick google along the lines of *installing grub 2*.

---

### Post by audiomick on 2009-12-22
Hi.
don't know for sure about that, but it could be.

There are instructions here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

for re-installing Grub2, which is what you will have on 9.10.

It is quite a long way down the page, re-installing, not installing which is near the top.

---

### Post by darkod on 2009-12-22
If you need more specific instructions can you please post the output of:
sudo fdisk -l

This first, second drive, then installed this on that, is difficult to follow. You should also take into account which drive you set as first choice in BIOS. I guess that part you missed when installing the win7. Windows always puts its bootloader on the disk first in boot order.
If you set your windows disk as first temporarily, the win7 shouldn't have touched your grub on the ubuntu disk.
Likewise, depending which disk you set as first and where you restore grub2 now, the BIOS can still keep calling the old broken grub2 from the other disk, and you might think the restore didn't succeed.

---

### Post by pognonec on 2010-01-04
> **darkod said:**
> If you need more specific instructions can you please post the output of:
sudo fdisk -l

Sorry for the confusion. Here we go:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89978   722748253+  83  Linux
/dev/sda2           89979       91201     9823747+   5  Extended
/dev/sda5           89979       91201     9823716   82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8019ff7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       89978   722748253+  83  Linux
/dev/sdb2           89979       91201     9823747+   5  Extended
/dev/sdb5           89979       91201     9823716   82  Linux swap / Solaris


The first boot HD in BIOS is sda. My current Ubuntu with all my documents and settings is on sdb. So how can I clean up/erase sda without disrupting my boot into Ubuntu that is on sdb, knowing that the only functional grub has been installed with Ubuntu on sda?

---

