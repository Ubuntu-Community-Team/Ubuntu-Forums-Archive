---
title: "Ubuntu 12.04 installer not detecting Windows 7"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by The2b on 2012-04-29
I'm currently running Ubuntu on my laptop exclusively, and I had just gotten a new desktop. It came with Windows 7 on it, and I decided to dual boot that with Ubuntu. But, I had a power outage that caused nautilus to stop working. This had happened before, and the fix was always just re-install Ubuntu. So, when I got the message on my laptop that there was a new version of Ubuntu, I upgraded that machine through Update Manager. Then, I went to upgrade the Desktop through UNetbootin to fix the nautilus issue. But, the only options it gave me were Erase HDD and start over or Something else. When I booted from the live CD (Technically USB) GParted said that the Windows NTFS partition had an I/O error. The first thought that hit me was to repair Windows 7. But, I didn't have a disk (The computer came with Windows 7). I tried chkdsk thru a bootdisk and it said everything was fine, no bad sectors. I installed he ntfsprogs package like GParted told me to, still no luck. Any idea on how to fix this?

EDIT: I went back again and I'm completely missing my /ect/mtab which GParted is saying would screw up the Windows detection

---

### Post by The2b on 2012-04-29
Well I fixed it by redoing the bootdisk. Must've been a corrupted download then...

---

### Post by Dimgeek on 2012-04-30
I have the exact same problem but recreating the install media didn't help. I compared the hashes from [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes") and they match.

I am not sure what is causing this. It just won't detect my Windows 7 installation at all.

---

### Post by jkorten on 2012-04-30
> **Dimgeek said:**
> I have the exact same problem but recreating the install media didn't help. I compared the hashes from [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes") and they match.

I am not sure what is causing this. It just won't detect my Windows 7 installation at all.


After the update - my system reports "no such partition" 3x (once for each boot device I suppose?).

I had windows installed on HD0 and Linux on HD1. Grub was also on HD1. It appears the upgrade writes a new grub on the HD0 (windows partition) and does so in a way that it has no idea what hardware is there.

Used the grub boot disk to put the windows MBR back in order. Now with the Ubuntu hard drive - I boot with the same "no such partition" error. I'm looking into this and will report back.

---

