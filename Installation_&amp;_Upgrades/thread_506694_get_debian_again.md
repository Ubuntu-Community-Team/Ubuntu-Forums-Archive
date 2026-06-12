---
title: "get debian again"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by sadden on 2007-07-22
hi i have a prob! give me the soloation. 
earler i had win xp and debian. then i formated my win xp(in drive c). after that i couldn't get my debian os. what shuld i do to get it agait with out reinstalling whole debian(my debian was in drive i)
thanks

---

### Post by 5-HT on 2007-07-22
It would be beneficial to describe the issue in a little more detail so that people can help you. From what you mentioned it appears that either your MBR got overwritten (shouldn't happen if you only reformatted a partition, but if it was a drive that's a different matter), oryour  bootloader on that partition (or drive?). You'll need to either reinstall a boot loader configured to boot both operating systems (i.e., GRUB, LILO). or configure windows to boot your debian install if that is the case.
cheers,

---

