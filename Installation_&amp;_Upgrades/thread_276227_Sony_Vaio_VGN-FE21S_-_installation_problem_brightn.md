---
title: "Sony Vaio VGN-FE21S - installation problem brightness adjustment"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by blackangel666 on 2006-10-12
Hello!

I've just installed Ubuntu Dapper Drake on my FE21S Notebook. But i wasn't able to install a software or the fn keys to adjust the brightness. I've already tried to use programs like smartdimmer or spicctrl. Nothing works. 
If i do adjsutments with smartdimmer the system will freeze and if i try it with spicctrl nothing will happen. It's really a problem because the brightness is now at the highest level and that's too much. 
The brightness adjustment in the power mangager also doesn't work. I also read some threads in this forum about such installation issues but nothing could solve my problem. 

I hope somebody can help me. 
Thanks!

---

### Post by gregorian21 on 2006-10-19
None of the methods described in forum postings work on my Sony VGN-FE28GP either. I am not a hardware/driver expert but I believe Sony has changed the implementation of the brightness control driver in the new latops which has rendered previous methods useless.

I've have had to go back to Windows until this issue gets resolved, as I can't stand to use the screen at maximum brightness. I tried Edgy, but that made no difference either.

Feisty Fawn (The next Ubuntu version) is expected to focus on improving laptop compatibility. Perhaps the situation might improve then or perhaps Sony could contribute a Linux driver. But until then, I'm having to live with Windows :(

---

### Post by nkvorn on 2006-10-21
Hello,

I had the same problem on my FE11s laptop. You can adjust the brightness by installing the latest nvidia drivers and changing the "nvidia-settings" -> "X Server Color Correction" -> "Brightness" value. It's not the best sollution but it works...  ;)

---

### Post by nkvorn on 2006-10-22
If you install the **lattest nvidia drivers** and **smartdimmer** then you can adjust the brightness using a command like *'smartdimmer -s **n**'* where **n** = 1..21.

It works great for my FE11s!!

---

