---
title: "another grub issue"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by noisehole on 2005-05-30
hi,
sorry for starting another grub thread, but i count find a solution for my problem:

i got 2 hdd's, one ide and one sata, /dev/hda & /dev/sda.
windows is installed on sda (win bootmanager too). the sata drive is setup as primary boot dev in bios.
i installed ubuntu to hda5 (no primary part on that disk) after changing primary boot dev to ide hdd in bios.

now i can boot without probs into linux (grub on hda mbr). the thing is that the win bootmanager doesnt seem to like switching the primary boot devices, so adding the w2k/xp boot loader to menu.list wont work (hda as primary bootdev).
conclusion: i need to add grub to the xp loader. but copying grub into a file using dd isnt working either. i guess thats because of the flipped boot order. (im getting 'GRUB hard disk error' that way).

so i wonder if there's any way to get a 'correct' grub for my setup somehow (with switched hdd's).

ps: using the exact same method works like a charm if i keep sda as primary boot device and install ubuntu in another primary part on the sata drive.

thx in advance

---

