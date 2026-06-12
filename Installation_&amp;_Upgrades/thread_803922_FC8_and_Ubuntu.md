---
title: "FC8 and Ubuntu"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by buccaneere on 2008-05-22
I loaded Ubuntu onto an HDD with FC8 already on it, and now when grub loads, it doesn't show FC8 as a boot option; only Ubuntu.

How do I fix this? All the dual boot how-to's do not show this scenario.

Thanks...........

---

### Post by Leetbumble on 2008-05-22
A little bit of detail is needed: (and i dont mean to be insulting or rude but often these things need to be asked)

Did you install ubuntu over top your FC8 install, in other words completely delete it?

**To test this I would use Gparted in ubuntu to check the size and make up of your hdd.

if you did find that FC8 is still installed there are pages on the forum about editing the grub boot loader. I had a similar problem after I removed vista from a second partition and wanted to expunge its name from my system completely. Its basically a text file.

two things you can try... 

Sudo update-grub

or

open: /boot/grub/menu.lst

this is the hard copy of the file that the shell command edits... I cant say more about adding FC8 to it but im sure someone better at this than me can pick up from here.

Hope this helped...

---

### Post by buccaneere on 2008-05-22
> Did you install ubuntu over top your FC8 install, in other words completely delete it?
No.

When Ubuntu is booted, the FC8 partition ( /boot ) still shows in the filesystem browser.

> or

open: /boot/grub/menu.lst

this is the hard copy of the file that the shell command edits... I cant say more about adding FC8 to it but im sure someone better at this than me can pick up from here.

This is what I need help on...

---

