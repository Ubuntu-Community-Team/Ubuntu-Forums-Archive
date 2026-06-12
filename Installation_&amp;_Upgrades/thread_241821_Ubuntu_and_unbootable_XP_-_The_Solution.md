---
title: "Ubuntu and unbootable XP - The Solution"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by Jonie on 2006-08-22
In my earlier post I described method to boot off XP on shared disk with Ubuntu, when it normally can't.

[http://www.ubuntuforums.org/showthread.php?t=239837](http://www.ubuntuforums.org/showthread.php?t=239837)

This has some caveats, however.

Floppy only seems to work physically this way, but actually reads no data.
Real floppy solution is little better, floppy works, unless it finds bad sector - XP bugcheks with STOP 7F immediately.

I spend some time to find, why some scenarios, especially when Linux is installed prior to XP (in terms of disk layout), make XP unbootable. The cause lies not in ntldr, but in NT partition bootstrap code. It tries to read partition table and hangs there, although in the partition table there is no real error. I don't know what causes this error exactly, it needs further debugging.

Then I managed to install patches to GRUB 0.97 from GRUB4DOS in Ubuntu, the one I was interested in, was the possibility to pick off ntldr directly and boot. NT partition mounting or using --edx option (this is virtually the same, the only difference is where ntldr is placed) is useless, since it fools XP to think it starts off hda1, where it isn't in fact. It just flashes "Invalid BOOT.INI" on the screen and restarts - ntldr doesn't find BOOT.INI.

Next, I coppied ntldr to my root partition /boot and just run nldr from there.


chainloader (hd0,0)/boot/ntldr
boot

Don't try it on unpatched GRUB - it won't recognize ntldr.

It boooooted!!! ntldr found active partition and ran OS from there.

Wouldn't it be nice to incorporate this patch to Ubuntu? It would solve a lot of questions "XP doesn't start anymore after install Ubuntu".

Jon

---

