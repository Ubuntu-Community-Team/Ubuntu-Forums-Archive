---
title: "after installation on PC, boot returns a blank screen"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by alain.roger on 2013-01-05
Hi,

as my windows 7 crashed yesterday, i decided to come to ubuntu 12.10 for my development computer.

first of all, to boot on dvd (ubuntu 12.10 x64) i needed to select "nomodeset".
then ubuntu is installing...

After reboot, blank screen :(

any idea ?

---

### Post by bogan on 2013-01-05
Hi!,** alain.roger,**

Check out this Sticky Thread, There is a step by step trouble-shooter in Post #1, and an index in Post #2:
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)

Does anything show on booting, before the blank screen?  Grub Menu ??

Can you get to a Consol [Text Terminal, TTY] with 'Ctrl+Alt+F1', or to a terminal with 'Ctrl+Alt+t',  or a cmd box with 'Alt+F2' ??

If so, please Post: ```
uname -ar
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Chao, [B]bogan.
[/B]

---

