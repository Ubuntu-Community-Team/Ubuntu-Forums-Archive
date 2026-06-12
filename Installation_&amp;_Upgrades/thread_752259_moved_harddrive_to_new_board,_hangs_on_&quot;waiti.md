---
title: "moved harddrive to new board, hangs on &quot;waiting for file system&quot;"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by chadmichael on 2008-04-11
I just bought a new motherboard and moved my IDE drive to it from an older ubunut system.  The machine boots up just fine but then cant find the root filesystem.  After hanging for a while on "waiting for filesystem" I get kicked out to a shell prompt and told that /dev/hda1 does not exist. 

My new board is an  Intel BLKDG33TLM LGA 775 Intel G33 Micro ATX Intel Motherboard - OEM and has SATA and one IDE channel.  The old drive is in the IDE channel, by itself.  And I have a new unformatted drive on the sata.  The behaviour appears the same with the SATA drive unplugged though.

---

### Post by David Robertson on 2008-04-11
Suggest you check your BIOS to make sure the IDE has the same settings as the previous board (probably AUTO) also check out the sata settings. Board can handle the mix of SATA and IDE in different ways. Your IDE drive may not be at the top of the list, which may confuse GRUB.

You could also try booting in recovery mode to access the drive. I think recovery goes for the drive's unique internal label regardless of where it is.

Hope this helps

---

### Post by chadmichael on 2008-04-11
I'll try recover mode.

As for the other stuff, if I'm getting through the kernel loading, etc., then Grub isn't confused is it?  It seems like its the mount stuff that is getting confused.

---

### Post by David Robertson on 2008-04-11
Have you tried running the install CD, running the desktop and checking you can access the partitions? This will tell you Ubuntu can handle the new board/old drive and also give you a chance to copy off your data.

I have reinstalled many times and kept or replaced my data. I normally keep:
/home (easy to do if in a separate partition - otherwise copy off elsewhere)
/var/cache/apt/archive (contains any package upgrades you have downloaded)

---

