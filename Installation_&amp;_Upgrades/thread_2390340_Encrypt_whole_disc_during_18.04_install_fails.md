---
title: "Encrypt whole disc during 18.04 install fails"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by boz_1812 on 2018-04-28
Ubuntu 18.04 LTS 64bit

During a clean install of 18.04 I chose to encrypt the whole hard drive.  After the install completed and I rebooted I was presented with the login dialog for my security key.  I entered the key and received the following message,
"cryptsetup (sda5_crypt): setup successfully"
The login hangs at this point and accepts no keyboard input, eg. Enter, Esp. etc.
Apologies for the poor quality photo.

Bob

---

### Post by harterc2 on 2018-04-28
I would get the menu in grub to appear.  Then edit the kernel boot parameters.  If it says splash try it without that and try verbose.
My boots hang with splash set.

---

