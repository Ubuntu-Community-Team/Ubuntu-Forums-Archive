---
title: "Mint on Hardware RAID1 not mounting properly"
date: 2015-04-30
forum: MINT
---

### Post by The Altruist on 2015-04-30
So, I have a hardware RAID1 and it's not loading up right. It took forever to get Mint to install, but I'm suspecting it didn't install right. Months later, the machine still works, but it's very flaky.

To preface,
I have 2xRAID1's (4 drives total) - one Mint Rebecca x64 KDE, one Win8.1x64.
Win8.1 works fine when I boot directly from it (more on that later).
I have a 5th hard-drive that just acts as a data drive. Also some externals. Let's assume they're more or less irrelevant. This happens when they're not plugged in.

Mint boots, but it complains of being unable to mount devices. Naively, I skip them.

But the system tends to freeze a lot. Turns out swap isn't mounting. That's when I realized something was wrong.

RAID Controller Info (lspci -v)
[http://pastebin.com/kudK9z0V](http://pastebin.com/kudK9z0V)

My hard drive listing (sudo fdisk -l)
[http://pastebin.com/bHb1gbCC](http://pastebin.com/bHb1gbCC)
The Linux RAID1 looks to be the second mapper set ( also /dev/sdc & /dev/sdd ) where nothing is recognized while the Windows RAID1 is the first ( /dev/sda & /dev/sdb ).

File System Table (cat /etc/fstab)
[http://pastebin.com/zf609D69](http://pastebin.com/zf609D69)
A different mapper name appears here which matches the one mentioned in GRUB (/dev/mapper/pdc_cfijddfag*) but it doesn't show up anywhere else.


GRUB listing (cat /boot/grub/grub.cfg)
[http://pastebin.com/qkQc7kPi](http://pastebin.com/qkQc7kPi)
It's using UUIDs and I'm pretty sure it's not supposed to be doing that.

My UUID list (sudo blkid)
[http://pastebin.com/DHtmE8h1](http://pastebin.com/DHtmE8h1)
/dev/sdd is separated into different partitions, but none of the others are.


Errors I noticed in Dmesg
[http://pastebin.com/dQANideY](http://pastebin.com/dQANideY)

What's Actually Mounted (mount)
[http://pastebin.com/yWB8FnLp](http://pastebin.com/yWB8FnLp)
Only /dev/sdd6 shows up.

OK, so.. /dev/sdd6 is my root, not /dev/mapper/pdc_cfijddfag6 or /dev/mapper/pdc_bdjhijafi1p*
My boot partition is being used but not mounted and the swap partition isn't being mounted at all. I CAN mount it manually.
/dev/mapper/pdc_bdjhijafi is my Windows 8.1 drive and that works fine when I boot straight from it - not so great when I try to boot from GRUB (looking at it now, the error is obvious, but the fix isn't).
The system completely doesn't understand /dev/mapper/pdc_cfijddfag*.
The ideal setup would be having Linux run in RAID1 with all the RAID1 benefits (faster reads! reliability!) and also the swap mounted properly.
How do I fix this?

EDIT: Apparently, I have FakeRAID. I will likely have to backup and reinstall from scratch. =(

---

