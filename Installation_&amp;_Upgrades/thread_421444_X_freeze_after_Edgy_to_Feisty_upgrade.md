---
title: "X freeze after Edgy to Feisty upgrade"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by pvdemael on 2007-04-24
Hi all,

I used to have a working Edgy installation with dual monitor support with an NVidia 6800XT card.
Recently, I upgraded to Feisty Fawn and got problems using the desktop manager.

I am able to log in using gdm or kdm (I tried both). After logging in, I see the default background color and the mouse cursor, gnome nor kde is booting. The mouse cursor is moving.

I searched the web for information without success. I installed the NVidia driver version NVIDIA-Linux-x86_64-1.0-9755-pkg2.run (other versions yielded an "incorrect version" error), I changed a lot of stuff to my xorg.conf and almost blew my brains out.

I decided to check which processes where running. Something strange popped up: There were more then 4000 entries showing:
pvdemael 31095  0.0  0.0      0     0 ?        Z    17:57   0:00 [xrd] <defunct>

The strange thing that I can log in using icewm, which I am using now to post this message.

I am really desperate as I really want to use Feisty.

---

