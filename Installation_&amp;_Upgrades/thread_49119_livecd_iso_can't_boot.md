---
title: "livecd iso can't boot"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by xash on 2005-07-15
has anyone tried the latest livecd iso?
i've tried it, burnt the cd with easycd pro, using all the "default" options on.

---

### Post by TheOtherShoe on 2005-07-15
I have successfully used a livecd shipped from Canonical. Can you give us some more information about what is going wrong? How far into the boot process do you get and are there any error messages?

You might also need to edit the BIOS options to change the boot device order so that your CD drive takes precedence over your hard drive. There is probably also a key that you can press during the boot to bring up a menu that allows you to select what device you want to boot from.

---

### Post by xash on 2005-07-15
[QUOTE=TheOtherShoe]I have successfully used a livecd shipped from Canonical.[/QUOTE]

I downloaded the livecd iso from a mirror.


[QUOTE=TheOtherShoe]
How far into the boot process do you get 
[/QUOTE]

To the installed os boot

[QUOTE=TheOtherShoe]
and are there any error messages?
[/QUOTE]

No error messages, the installed os boots

[QUOTE=TheOtherShoe]
You might also need to edit the BIOS options to change the boot device order so that your CD drive takes precedence over your hard drive. There is probably also a key that you can press during the boot to bring up a menu that allows you to select what device you want to boot from.[/QUOTE]

I did it. I also eliminated the hd from the boot device order list. Same result.
Just to mention, the cd autoplay works.

---

### Post by TheOtherShoe on 2005-07-16
What motherboard / BIOS software and CD drive are you using? This sounds like a BIOS or hardware specific problem.

---

### Post by javiadip on 2005-07-16
[QUOTE=xash]has anyone tried the latest livecd iso?
i've tried it, burnt the cd with easycd pro, using all the "default" options on.[/QUOTE]

did you try checking ISO image's integrity by running md5 checksum, your image might be corrupted

---

