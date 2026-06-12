---
title: "Laptop won't boot after trying to install 14.04 to dual boot with Windows 8"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by twisted willow on 2014-04-29
I threw caution to the wind this morning and tried to install Ubuntu on my Windows 8.1 laptop to dual boot (HP Pavillion g7). During the install I manually configured the partitions, picking on I was pretty sure I created a few monthsd ago after an earlier failed attempt to install Ubuntu. Needless to say it's all gone wrong. This is what I have had and tried so far:

[LIST]
[*]Neither Ubuntu or Windows would boot initially. Ubuntu appeared in the startup menu but threw an error. Windows 7 and 8 were also options but didn't work
[*]I booted into the live DVD and ran Boot Repair. This got the windows login screen back but this then flashed a blue error screen and went into repair mode
[*]I couldn't run any of the repair tools, getting an error message to say the drive is locked
[*]I tried a DOS programme called Diskpart - this gave a status of invalid for my hard drive
[*]I tried CHKDSK /f but this wouldn't run. CHKDSK came back with something like errors in the uppercase file
[/LIST]

I unfortunately don't have a Windows 8 disk as I downloaded only when I purchased it and haven't made a recovery disk (stupid I know).

I can still access the data on my hard drive (photos, music, etc) via Ubuntu live.

Worst case scenario I can back up the data on an external hard drive I have and reinstall everything from scratch, but is there anything I can try before this? I guess when I set up the partitions I inadvertently overwrote the MBR or something - a little knowledge is a dangerous thing as they say!

---

### Post by oldfred on 2014-04-29
Post link to BootInfo report from Boot-Repair so we can see where you are at.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

