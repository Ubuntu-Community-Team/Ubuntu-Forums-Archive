---
title: "Garbled Graphics at Boot up"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by Moses747 on 2006-06-29
Hi I'm new to Linux, I've just installed Dappler 6, 64 bit version, install went perfect but after rebooting and selecting OS from Grub the bootup screen is totally garbled, unreadable, can someone please advise on a fix.
I have an Asus A8N-SLI Premium Motherboard, Nvidia FX6800 128MB Graphics Card, 1GB RAM, AMD 64 3000+, 2x250GB Harddrives.

---

### Post by DSn0wMan on 2006-06-29
Can you press "ctrl + alt + f1" and get a prompt?

---

### Post by Moses747 on 2006-06-29
Not sure, haven't tried that yet, not too familiar with Linux commands etc, I've only ever used Windows, Linux is totally new to me lol.

---

### Post by DSn0wMan on 2006-06-29
[QUOTE=Moses747]Not sure, haven't tried that yet, not too familiar with Linux commands etc, I've only ever used Windows, Linux is totally new to me lol.[/QUOTE]

hitting "ctrl+alt+f1" should put you in single user mode (text only). That way if it's you graphics card that is giving you problems you can reconfigure it.

If "ctrl+alt+F1" works, just log in and then type ```
 dpkg-reconfigure xserver-xorg
```

That will start a text based wizzard to help you configure your graphics/keyboard/mouse settings.

---

### Post by Moses747 on 2006-06-29
Ok thanks for that, will give it a go and see what happens. Will let you know if it works.

---

