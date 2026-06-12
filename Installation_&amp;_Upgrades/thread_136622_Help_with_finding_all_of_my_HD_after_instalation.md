---
title: "Help with finding all of my HD after instalation"
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by Entrail on 2006-02-26
I once installed ubuntu, but I had a problem then and had to install WinXP again.
I had 2 hd's on 200GB each. After the installation I found the 189GB on one of the HD's in my home folder, but the ubuntu OS had taken all of my other HD to install the OS on.

This is what I want to know:
Is there a way I can install ubuntu without having to let go of so much of my HD? I have a total of 5 partitions now in WinXP. Can I install ubuntu on one of them and be able to locate all of the outher HD's? Will 30GB be enough for installing ubuntu? Do I have to format the windows partitions to find them in ubuntu?

Sorry for bad English.

---

### Post by DaBruGo on 2006-02-27
[QUOTE=Entrail]I once installed ubuntu, but I had a problem then and had to install WinXP again.
I had 2 hd's on 200GB each. After the installation I found the 189GB on one of the HD's in my home folder, but the ubuntu OS had taken all of my other HD to install the OS on.

This is what I want to know:
Is there a way I can install ubuntu without having to let go of so much of my HD? I have a total of 5 partitions now in WinXP. Can I install ubuntu on one of them and be able to locate all of the outher HD's? Will 30GB be enough for installing ubuntu? Do I have to format the windows partitions to find them in ubuntu?

Sorry for bad English.[/QUOTE]

Entrail,

I have a setup guide you may be able to adapt to work for your situation. Follow the link below in my signature lines.

Hope it helps,
DAVE

---

### Post by Entrail on 2006-02-28
Ok, I think I understood it, but cant I just install ubuntu on one of my HD's without having the outher HD inside and put in the outher HD later and format it then? If I do this will I be able to locate it?

---

### Post by DaBruGo on 2006-02-28
[QUOTE=Entrail]Ok, I think I understood it, but cant I just install ubuntu on one of my HD's without having the outher HD inside and put in the outher HD later and format it then? If I do this will I be able to locate it?[/QUOTE]

Entrail,

Yes you can do that. Actually, that may be the best way (having just the HD connected that you want to load Ubuntu on) because the GRUB bootloader will correctly setup all the HD settings in it's menu.lst file for you.

If you do add another HD later to your PC, I would highly suggest that you leave the HD (with Ubuntu on it) as the first HD in your system. It helps keep GRUB from getting messed up on it's settings

Hope that helps,
DAVE

---

