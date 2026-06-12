---
title: "In need of assistance"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by runesvend on 2007-04-16
Hello

I've just installed Ubuntu Edgy Eft on my machine but I can't get it to boot without a floppy because of a RAID controller on my motherboard messing up the boot sector on my hard drives. I've found a workaround described in the link below but I'm having a hard time following what exactly it is he does and I'd appreciate if someone could make it a bit more clear so I can do what he says will fix this problem.

Here's the link: [http://lists.gnu.org/archive/html/bug-grub/2004-07/msg00113.html](http://lists.gnu.org/archive/html/bug-grub/2004-07/msg00113.html)

Thanks in advance!

-Rune

---

### Post by dozch on 2007-04-16
What exactly are you trying to achieve?

* If you only have one hard drive then I would try to turn off RAID support in the BIOS

* If you try to setup Edgy on a RAID array then follow the steps in the [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

It's pretty laborious and I would recommend to wait until Feisty is released. Feisty has a at least a working dmraid package, which is used to manage the RAID drives, and you won't have to go through the same if/when you want to upgrade.

---

### Post by Detonate on 2007-04-16
I do not see any need for RAID on 99% of the home computers out there.   I do not know why it seems to come as the default for PC installations these days.  Just causes problems.  Turn it off.

---

### Post by runesvend on 2007-04-16
The RAID is disabled, but it still won't work. I'm not interested in using RAID, just to get it working when my hard drives are connected to the RAID controller. I only have two IDE connectors that are utilized by my two DVD drives. Even when RAID is turned off the RAID controller still does this, as it says in the link:

"[I]After some hard testing I detected, that four bytes - namely the bytes
0x1220+3 - of /dev/hde are overwritten with zeros at booting time.[/I]"

So I'm not interested in using RAID, I'm just interested in being able to boot Ubuntu from my hard drives rather than from a floppy.

---

