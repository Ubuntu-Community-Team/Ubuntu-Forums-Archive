---
title: "Ubunto on USB Drive but won't boot forgot to do advance bit in install what do I do"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by kin777 on 2010-04-13
I'm on Windows XP and don't have enough room on my HD to install ubuntu so I decided to put it on an external USB drive - but when I did it I didn't know about the advanced bit in the install so when I tried to boot I destroyed my MBR for windows and it wouldn't boot - so I did fixmbr from the windows recovery console and now I can boot into windows but can't boot from the USB Drive - ANY IDEAS?

Many Thanks
Kin

---

### Post by bumanie on 2010-04-13
You can boot an ubuntu live cd and install grub to the correct place, ie the external drive, but the method of doing so differs, depending on whether you are using grub-legacy or grub 2. If using ubuntu 9.04 or earlier, it is likely you have grub-legacy, if you have installed 9.10, grub 2 should be the version. If you can state which grub you have, someone will be able to help.

---

### Post by kin777 on 2010-04-14
Hi Thanks for the response I have the Ubuntu 9.1 CD - I guess that means I have grub 2? Where do I go from here? My Bios is set to boot from USB.

---

