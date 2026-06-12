---
title: "Installing Ubuntu and Suse"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by docmur on 2005-09-07
Okay so like my title says I want to have 2 linux installs.
right now I have a 200 GB IDE drive with WinXP and Suse 9.2 pro on it
I'm going to remove the WinXP so to free room.
Now how would I make it so Suse 9.2 pro can share with Ubuntu????
Oh I use grub

Thanks 
DOCMUR

---

### Post by essexman on 2005-09-07
[quote=docmur]Okay so like my title says I want to have 2 linux installs.
right now I have a 200 GB IDE drive with WinXP and Suse 9.2 pro on it
I'm going to remove the WinXP so to free room.
Now how would I make it so Suse 9.2 pro can share with Ubuntu????
Oh I use grub

Thanks 
DOCMUR[/quote] 
The Horey (Ubuntu 5.04) installation should do this automatically. Best to keep a copy of the /boot/grub/menu.lst file in your suse inststallation. If anything does go wrong, which it shouldn't, you can manually add the suse entry into your new Ubuntu menu. The Installation will identyfy your swap partition as well.

all the best

Essexman

---

