---
title: "BIOS wont boot from cd drive, need to install XP"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by fbp90crx on 2008-11-17
I currently have Ubuntu hardy on my desktop and I need to install xp because there are programs I need for school that are windows only. I got ubuntu working on my macbook so I'm not giving up on ubuntu, it works better on my macbook anyways (old desktop). I have an OEM XP Pro cd but evidentially my bios doesn't recognize my cd drive because even when I set the boot priority to boot from the cd, it goes straight to booting ubuntu (from the HD). I did have to replace the oem cd drive a couple years ago and it works perfect in the OS but the BIOS won't boot from it.
So, 1. how can I make my bios recognize my cd drive or 2. how can I install XP from inside Ubuntu
Thanks in advance!

---

### Post by Yownanymous on 2008-11-17
To be honest, school-wise, there's pretty much nothing Windows can do that Ubuntu can't. Microsoft just want you to think it's all Windows exclusive.

---

### Post by Arcturus691 on 2008-11-17
Not sure what kind of a system you have but you may want to go into the bios at bootup and make sure the CD is set as the first boot device.

CAUTION :twisted:
Microsoft does not play nice with other OS's  Once XP is installed you will no longer be able to boot into ubuntu becuase XP overwrites the Master Boot Record, thus you lose Grub or any other bootloader for that matter.  

If you get XP installed and want to be able to boot Ubuntu as well, let me know and I can walk you through putting Grub back.  It is a little on the technical side but is not that hard to do.

---

### Post by Sirhanz on 2008-11-17
Have you checked the drives jumper settings are correct? I've seen cases where a drive was set improperly to slave/ master where the bios wouldn't detect it but then Ubuntu straightened it out once booted. Also I have no idea as to your set-up, i.e. hd's dvd, cd, etc. Nor if they are ide or sata, Also I have had problems with some installs, with ubuntu actually, where I have to unplug a cardreader or other accessory to complete an install.

---

### Post by fbp90crx on 2008-11-17
Thanks guys! It was just the jumper setting.

---

### Post by Arcturus691 on 2008-11-18
> **Sirhanz said:**
> Have you checked the drives jumper settings are correct? I've seen cases where a drive was set improperly to slave/ master where the bios wouldn't detect it but then Ubuntu straightened it out once booted. Also I have no idea as to your set-up, i.e. hd's dvd, cd, etc. Nor if they are ide or sata, Also I have had problems with some installs, with ubuntu actually, where I have to unplug a cardreader or other accessory to complete an install.

](*,):lolflag:
Darn should of checked the physical layer first when troubleshooting.  Good catch

---

