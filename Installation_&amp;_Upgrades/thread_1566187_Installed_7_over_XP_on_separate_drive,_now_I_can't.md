---
title: "Installed 7 over XP on separate drive, now I can't get into Ubuntu"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by TonyChaos on 2010-09-02
Hey guys,

I recently decided to get Windows 7 Ultimate to upgrade from XP. I have two drives in my machine. One has Ubuntu, the other XP. I upgraded the XP drive to Windows 7 and now I can't boot into my other hard drive to get into Ubuntu.

The way I had it before I was using GRUB to pick between my Ubuntu drive and my Windows drive at startup. It's not giving me the option now. I even tried cracking the machine open and getting at the guts of it to unplug my Windows drive hoping that it'd just work itself out that way and I could change the GRUB around a bit. No such luck. It gave me this weird image. You may have to look closely, as the only camera I had handy at 2:30AM was the one on my BlackBerry.

Please help! I have about 400GB of stuff on my other drive that I need. Thanks!

Here is a picture of what comes up when I try to get into my Linux drive. Any tips or help would be really appreciated.

[ATTACH]168212[/ATTACH]

---

### Post by wilee-nilee on 2010-09-02
It sounds like you had the grub bootloader in the master boot record=mbr of the XP hard drive.

You need to confirm the type of grub in Ubuntu; whether it is grub-legacy (came with Jaunty) or grub2 karmic and beyond unless you upgraded to it. Once you have that you can load the correct grub to the same hard drives mbr as Ubuntu and put it first to boot. Here is a link that should help.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

