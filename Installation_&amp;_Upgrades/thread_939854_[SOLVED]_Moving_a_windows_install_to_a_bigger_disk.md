---
title: "[SOLVED] Moving a windows install to a bigger disk"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by ssam on 2008-10-06
I have been asked to install ubuntu on a computer
hp pavilion a405.uk
768MB ram
40GB IDE disk
2.5Ghz celeron

It currently has windows XP on it, and i'd like it to dual boot. I have been doing linux installs for years, but i have very little experience with windows.

There is not enough space on the disk to just resize windows' partition and add a linux one, so it is going to need a hard upgrade. I had a look inside, and it seems that it can only comfortably fit a single hard disk.

So i think i'll need to move the windows partition to the new disk. here is how i imagine it might work.

boot the machine from an ubuntu live cd.
connect new disk through a USB addapter.
create a partition layout on the new disk, with a partition exactly the same size as the current windows partition
dd the windows partition from the old drive, to the new.
switch off, take out the old drive, put the new one in.
now boot from the ubuntu installer, and install ubuntu.

will this work?
will windows still boot?
will windows demand reactivation?

---

### Post by caljohnsmith on 2008-10-06
You really don't need to even make a partition for Windows on your new HDD, because I would assume you want to also copy the MBR (Master Boot Record) from the old HDD so your new HDD will be bootable. I would use dd to do a perfect clone of the old drive using something like:
```
sudo dd if=/dev/sda of=/dev/sdb bs=10M conv=notrunc
```
And of course *make sure* you get the input/output drives correct or you will forever lose your current Windows. :) I've used the above command to clone a friend's HDD, and it worked perfectly. If the new drive is larger than the old one (it needs to be at least as big), I would get Windows booting first, and once you can do that, you could use gparted to expand Windows' partition to fill the whole HDD. 

Since you are going to take out the old drive and replace it with the new one that will have your cloned Windows on it, you hopefully won't have any problems booting it since the Windows drive letter should still be the same. If you do run into problems, here are a few links that might fix the issue:

[http://support.microsoft.com/kb/223188/EN-US/](http://support.microsoft.com/kb/223188/EN-US/)
[http://www.goodells.net/multiboot/partsigs.htm](http://www.goodells.net/multiboot/partsigs.htm)

Let me know how it goes. :)

---

### Post by ssam on 2008-10-06
Thanks.

That sound very simple. I wonder though, if the MBR is copied, will it not make the new drive look like it is only 40GB, or gparted smart enough to sort this out.

---

### Post by caljohnsmith on 2008-10-06
> **ssam said:**
> Thanks.

That sound very simple. I wonder though, if the MBR is copied, will it not make the new drive look like it is only 40GB, or gparted smart enough to sort this out.
Your cloned drive will have the exact same size Windows partition on it as the old Windows drive, but I believe gparted will see the new HDD size, so if the new HDD is larger, you should be able to use gparted to increase the Windows partition to fill the whole drive.

---

### Post by ssam on 2008-12-26
it worked :-)

i booted with the ubuntu cd. plugged in the new disk with a USB-IDE adapter. made sure neither disk was mounted. used dd to copy sda to sdb. then shutdown, took out the old disk, and connected the new disk to the real IDE bus.

windows booted fine, as if nothing had happened. then i used the gparted livecd to enlarge the windows partition, and make linux partitions.

---

