---
title: "How to edit the menu.lst?"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by larrylamsy on 2010-04-10
Hi, I learnt from a BSD magazine and installed PCBSD on my Dell notebok a single harddisk with a hope to have a triple boot. I have all the three OS, but could not find the menu.lst from /boot/grub/....

All I can find is a grub.cfg which is not editable. Someone from this forum said that menu.lst = grub.cfg.  Is that true? I would be very grateful if someone can offer me a help to teach me "step by step" to edit the grub.cfg.  Thanks. :confused:

---

### Post by howefield on 2010-04-10
> **larrylamsy said:**
> Someone from this forum said that menu.lst = grub.cfg.  Is that true? I would be very grateful if someone can offer me a help to teach me "step by step" to edit the grub.cfg.

Grub.cfg is the replacement for menu.lst in the latest version of grub but as you already know isn't meant to be edited.

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by larrylamsy on 2010-04-10
Thanks Howefield. I thought open source would give more freedom to users to make modifications so to fit their needs. But thanks any way.

---

### Post by howefield on 2010-04-10
> **larrylamsy said:**
> ...would give more freedom to users to make modifications...

Than what ?

I think you'll find it does, and you know it :)

---

### Post by tommcd on 2010-04-10
> **larrylamsy said:**
>  I thought open source would give more freedom to users to make modifications so to fit their needs. But thanks any way.
You still have all the freedom you want with grub2. Did you *read* the link that Howefield gave you: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
And here is another excellent tutorial:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
If you want to edit the boot options for grub2, you need to edit the **/etc/default/grub** file.
If you wish to add custom entries to boot another operating system, you can either add them to the **40_custom** file in the /etc/grub.d directory, or create your own executable file in the /etc/grub.d directory.
Those 2 tutorials I linked to provide excellent info on how to do that.
If you want to boot a BSD based OS from Ubuntu's grub2 though that may require special consideration not covered in those tutorials. Perhaps PCBSDs documentation could provide more info on that.

---

