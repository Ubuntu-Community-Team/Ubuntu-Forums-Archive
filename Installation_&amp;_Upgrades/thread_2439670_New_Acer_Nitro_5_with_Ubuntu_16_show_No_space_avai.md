---
title: "New Acer Nitro 5 with Ubuntu 16 show No space available 0.0KB"
date: 2020-03-31
forum: Installation &amp; Upgrades
---

### Post by khutpidor on 2020-03-31
[COLOR=#242729][FONT=Arial]I tried to set up new Acer Nitro 5 with Ubuntu16 (Fresh Set Up), but no space of a storage is show up.

Bios Information: [https://i.stack.imgur.com/0FRYA.jpg](https://i.stack.imgur.com/0FRYA.jpg)
Error Screen: [https://i.stack.imgur.com/kQ5ge.jpg](https://i.stack.imgur.com/kQ5ge.jpg)[/FONT][/COLOR]

---

### Post by QIII on 2020-03-31
Hello!

Did your machine come with a pre-installed operating system?  What OS?

---

### Post by khutpidor on 2020-03-31
> **QIII said:**
> Hello!

Did your machine come with a pre-installed operating system?  What OS?

No dear, 
It came with nothing installed since I just bought it

---

### Post by deadflowr on 2020-03-31
Change the SATA mode to AHCI if you can.
Linux can't use RST, as far as I remember.

---

### Post by khutpidor on 2020-03-31
> **deadflowr said:**
> Change the SATA mode to AHCI if you can.
Linux can't use RST, as far as I remember.

I see, 
I also try to look for a way to switch, but couldn't find one. 
Normally, first they have Window install while I came with nothing. 

On my BIOS tab MAIN, I see no such an option to switch SATA type

---

### Post by khutpidor on 2020-03-31
I could solve the Problem by follow this link
[https://community.acer.com/en/discussion/579607/change-sata-mode-from-rst-to-ahci](https://community.acer.com/en/discussion/579607/change-sata-mode-from-rst-to-ahci)

Thank You

---

