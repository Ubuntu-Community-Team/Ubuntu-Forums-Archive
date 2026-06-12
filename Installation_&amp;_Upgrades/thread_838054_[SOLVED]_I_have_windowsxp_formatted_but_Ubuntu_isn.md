---
title: "[SOLVED] I have windowsxp formatted but Ubuntu isn't opening"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by sowhat12345 on 2008-06-23
I have my xp formatted again like every month :( Before I formatted my xp when I popen my computer I can select which operation system I want. But after I format windowsxp that page isn't coming . So I can't select the Ubuntu to start and W&#304;ndows xp is opening automaticly . I installed the ubuntu in the free space ,I mean it isn't installed in C(xp's part) and D(2.part). I installed in the free sapce.What should I do now ?:confused:

---

### Post by sowhat12345 on 2008-06-24
I solved the problem myself . I write it :

open with live CD Ubuntu
open the terminal
type xterm
type sudo grub
find /boot/grub/stage1
The result like : (hd0,2)
type root(hd022)
setup(hd0)

Thats all :)

---

