---
title: "Triple boot issue (Win10+Ubuntu+Elementary)"
date: 2020-05-15
forum: Installation &amp; Upgrades
---

### Post by wojo90 on 2020-05-15
Hi I have win10 on my SSD drive. In place of blu ray drive I have a hard disk mounted 1TB. I wanted to use this disk for various linux distributions. And so I have installed elementary OS and then Ubuntu using option: "Install Ubuntu alongside Elementary". Default options. Next I divided the disk partition about 50% for Ubuntu and Elementary. After all the grub bootloader doesn't start. Win10 automatically turns on. The only solution I figured out is to change boot order (Ubuntu before Windows Boot Manager), then grub starts but I can only choose between Ubuntu and Elementary. Is it possible to have 3 OSes in this way? And what to do to be able to choose between 3 different OSes in one bootloader?

---

### Post by CelticWarrior on 2020-05-15
Welcome.

Please turn off Fast Startup in Windows the change the boot order back to Ubuntu, boot Ubuntu and run ```
sudo update-grub
```.

---

### Post by wojo90 on 2020-05-16
I had Fast Startup turned off. S[COLOR=#000000][FONT=&quot]udo update-grub solved the problem. Thanks a lot[/FONT][/COLOR]

---

