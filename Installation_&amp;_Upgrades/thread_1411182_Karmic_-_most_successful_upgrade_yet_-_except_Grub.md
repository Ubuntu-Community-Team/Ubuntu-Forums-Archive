---
title: "Karmic - most successful upgrade yet - except Grub..."
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by mango42 on 2010-02-19
Just upgraded from 9.04 to 9.10 - everything works fine. Thanks to the Ubuntu team for such a remarkable achievement.

And now I have to go and spoil it. I have three working partitions: XP on primary, this upgrade on sda5 and a (previous) fresh install of UbuntuStudio 9.10 (with GRUB2, ext4) on sda7.

On upgrading sda5, old GRUB finds XP okay but totally ignores my UStudio partition.

I would be fine with the other way round, yet every upgrade since 6.06 has ignored other partitions... ;-)

So how do I get the old GRUB, installed by the 9.10 upgrade on sda5, to recognise sda7 and put it in its menu.lst ?

At present I'm just booting sda7 from Grub's commandline with the root | kernel | initrd | boot sequence - tedious yet powerful :confused:

ps: Can provide 'non-classified' parts of Results.txt output from boot_info_script055.sh if it would help clarify all this?

---

### Post by darkod on 2010-02-19
Unless specifically upgraded too, grub remains as grub1, it doesn't upgrade to grub2. And as far as I know, grub1 doesn't automatically add OSs later, that's the new feature of grub2.
So you would need to create an entry for Studio in your grub1 menu.lst that you are still using.

---

### Post by mango42 on 2010-02-20
Greetings, darkod - it's many years since I visited Sophia but I still remember the incredibly warm and selfless hospitality I received in very difficult circumstances ;-)

Fair enough comment but my question is why GRUB 1 can never 'find' these other partitions at upgrade time. There's **df**,**blkid** and no end of other commands for seeing what is on an HDD...

---

### Post by darkod on 2010-02-20
> **mango42 said:**
> 
Fair enough comment but my question is why GRUB 1 can never 'find' these other partitions at upgrade time. There's **df**,**blkid** and no end of other commands for seeing what is on an HDD...

Well I guess that's why a new version was finally released. Although people accustomed to grub1 are criticizing grub2 right now. It was necessary to release a new version because grub1 is older than 7-8yr I believe.

---

