---
title: "Erase disk and install ubuntu not working as expected"
date: 2019-06-24
forum: Installation &amp; Upgrades
---

### Post by david-holm on 2019-06-24
Hey guys! New around the block, trying to get this to work.

So I currently am running Windows 10 on my machine but want to switch over to Ubuntu. I’ve created a bootable usb using Rufus and booting into it seems fine. But when I can choose erase disk and install Ubuntu and I press install it says that the partitions that are going to be formatted are the ones on my usb. I tried that but when I restarted my machine it went into minimal grub terminal. I could also still boot into windows so obviously the disk was not formatted at all. All my files were still intact.

Tried to manually create partitions but it’s been giving me a hard time there as well. 

Ubuntu version is 18.04.

Any ideas?

---

### Post by Bashing-om on 2019-06-24
david-holm; Hello -

Two - maybe 3 - ideas:
1) secure boot disabled in bios ?

2) Windows is completely shut down such that "fast start" is not a factor ? As fast start is actually hibernation and Windows still has a lock on the drive.

3) When you boot the liveUSB - boot menu -> "check disk for defects" completes with no errors?

4) An Acer machine ? where "trust" must be set in bios ?

[INDENT][INDENT]could be this, 
[INDENT][INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by david-holm on 2019-06-24
Thanks for the input! I will try that out and see how I fare.

---

### Post by oldfred on 2019-06-24
Often systems need UEFI updates & SSD firmware updates (if SSD).

What brand/model system? What video card/chip?

---

### Post by grenic on 2019-06-24
FYI: [https://ubuntuforums.org/showthread.php?t=2421578](https://ubuntuforums.org/showthread.php?t=2421578)

---

