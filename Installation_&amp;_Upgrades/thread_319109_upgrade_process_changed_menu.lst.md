---
title: "upgrade process changed menu.lst"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by spx3 on 2006-12-15
it seems that for no understandable reasons the last upgrade i did
had modified my /boot/grub/menu.lst
i was able to see this by chance only because i had made some changes
prior to the upgrade that prevented my mouse from not working,and suddenly
it didn't worked(as i posted here [http://ubuntuforums.org/showthread.php?t=319048](http://ubuntuforums.org/showthread.php?t=319048) ).
i am curious if other unpleasant changes are made by an upgrade.
also is there anyone else who has had the same problem(upgrade changing
something unexpected) ?

---

### Post by ZERO_SHIFT on 2006-12-15
Well upgrading speeded boot time.

---

### Post by tanas on 2007-01-10
I had exactly the same thing happening yesterday (hadn't used this for 2 weeks).
But my change was quite dramatic: the windows boot option just disappeared from menu.lst!!
i have no clue how i'm going to get it back (i didnt had a copy of menu.lst).

---

### Post by arnieboy on 2007-01-10
post the result of the following:
```
sudo fdisk -l
```

---

### Post by tanas on 2007-01-10
Thanks!.. That would have given me some hint! (I read your post too late)
I just remembered (before reading your post) that my Acer Laptop has an extra partition called pqservice where pre-installed windows is stored.
So my windows partition was actually in (hd0,1) and not in (hd0,0) as I was trying in my menu.lst

thanks anyway!!

---

