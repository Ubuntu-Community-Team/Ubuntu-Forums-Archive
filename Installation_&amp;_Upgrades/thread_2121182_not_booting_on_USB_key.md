---
title: "not booting on USB key"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by Autumn319 on 2013-03-01
Good morning,
i have put a LTS ubuntu 12.04 edition on a usb key and i have succeeded to install it on two computers.
Then i have tried to install it on a on asus f55vd-sx217h  ,the processor is a [COLOR=#909091][FONT=Arial]Intel® Pentium® Processor B980/ 2,4GHz / 2Mb / 35W / 2 core / 2 Thread.
[/FONT][/COLOR]I have changed the boot sequence to have the usb key first in the sequence.

When the computer restarts,the little light on the usb key is on and then,nothing,and it boots on windows 8.
any idea?i don't have have any.
Thank you in advance.

---

### Post by Seborreia on 2013-03-01
You probably have to configure the boot security. Go onto BIOS setup (if it came with windows 8 it is probably a EUFI setup though). And you would have to follow the windows 8 instructions to install it, which is a bit different: [https://help.ubuntu.com/community/UEFI#SecureBoot](https://help.ubuntu.com/community/UEFI#SecureBoot)

---

### Post by Autumn319 on 2013-03-01
thank you for the answer!
i have disabled the secure boot and it doesn't work.
it keeps on booting on windows8.:(:confused:

here are photos of my bios:
[IMG]http://i21.photobucket.com/albums/b289/gibsonian/informatique/2013-03-01160040_zps61e9797b.jpg[/IMG]

[IMG]http://i21.photobucket.com/albums/b289/gibsonian/informatique/2013-03-01160012_zpsc9d676de.jpg[/IMG]

---

### Post by Malo Kingi on 2013-03-01
Autumn319, I've been looking for the same answer as you, and I found this ([http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)). Seems like it's the way to go for a usb stick install. I'll be trying it when I get home from work. Good luck.

---

