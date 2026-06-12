---
title: "delete grub"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by chuchi on 2011-08-08
hi friends!! I've got a computer for only two months,and after that, I have to get it back. It has installed only Windows XP, and as you suppose, I want to install Ubuntu!!! But when I get it back, I don't want the owner to know I installed Ubuntu.

Is there any way to uninstall the grub so that only the Windows loader is working??

thank you very much!!

---

### Post by MG&amp;TL on 2011-08-08
This, I'm afraid, is somewhat problematic, and IMO should be made a LOT clearer on the ubuntu download page. From here onwards, I am assuming that you did a normal install, i.e a partition, rather than wubi.

 If you have a windows xp installation disc,  I suggest backing up EVEERYTHING and doing an 'upgrade' from windows XP to windows XP.

If not, I found a 'recovery' .iso on the web. Burn a cd and boot from it. Get a command-line from it and run: 

```
./fixmbr
```

Which 'fixes' the MBR of windows, stopping grub. Or at least it did for me. Then boot into windows without the cd, remove ubuntu partitions from there and expand the windows partition. In this case, back EVERYTHING up as well, in case of failure.

Please note that this worked with windows7, I have no clue whether this will work on XP, but a recovery .iso should be considerably easier to source. If you have a 'recovery partition' use that, but with extreme caution.

Of course, you could always hope that he/she likes it. :)

Good luck!

---

### Post by sikander3786 on 2011-08-08
Instead of messing up some-one else's PC, I would suggest to at least replace the HDD with your own and install Ubuntu onto that. Later, you can pull out your HDD and place the original one back.

No one can guarantee you that installation of Ubuntu would not break any thing previously contained on the HDD including the other OS, MBR, personal files etc. Why risk some-one else's data?

---

### Post by YesWeCan on 2011-08-08
> **chuchi said:**
> hi friends!! I've got a computer for only two months,and after that, I have to get it back. It has installed only Windows XP, and as you suppose, I want to install Ubuntu!!! But when I get it back, I don't want the owner to know I installed Ubuntu.

Is there any way to uninstall the grub so that only the Windows loader is working??

thank you very much!!

If you do not have an XP install CD, check the name of your disk in Disk Utility - it is probably /dev/sda
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

