---
title: "Grub Error 17"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by El King on 2008-04-28
hey everyone am dual booting Windows and Ubuntu "Hardy"
i was running out of space on the hardy partition so i resized it and added a few gigs to it. after that i cudnt boot, the grub loader wud come with an error 17 and just stops.
i had to boot with a windows cd and fixmbr and now ofcourse the grub is gone, wat can i do to get the grub loader back working ?!
Thanks

---

### Post by darkelvenangel on 2008-04-28
Frist off you'll need to boot off your linux CD then you'll need to reinstall Grub.

This thread should help you out.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Pumalite on 2008-04-28
Stay on your Live CD and follow the link.

---

### Post by El King on 2008-04-29
can i use the live cd from the gutsy ?!
i lost the hardy iso and am too lazy to download it again

---

### Post by Pumalite on 2008-04-29
Yes.

---

### Post by El King on 2008-04-29
i tryed and it gave ma an error 12
i guess the partition needs to be formated after it has been resized, seems this change in space caused some corruption or i duno  :S
Thanks anyway i will format and install hardy again

---

### Post by Pumalite on 2008-04-29
Error 12 means that you are trying to boot Windows from a logical partition. Windows requires a primary partition.
Post a screen shot of Gparted.

---

### Post by El King on 2008-04-30
i made a backup jus before things go bad so i recovered it from windows and then re-formated and re-installed hardy and things are going fine now
Thanks Pumalite

---

### Post by Pumalite on 2008-04-30
You are welcome. Good luck.

---

