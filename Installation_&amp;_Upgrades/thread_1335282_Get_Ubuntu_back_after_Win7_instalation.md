---
title: "Get Ubuntu back after Win7 instalation"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by aneslin85 on 2009-11-23
guys, in my laptop I used Vista, and I installed Ubuntu with wubi.
and yesterday I did a win7 clean instalation. 
so its overwrite my old bootloader / grub

so, how can I get my ubuntu back ? without instaling it again.
thank you.

---

### Post by ptn107 on 2009-11-23
If 'sda' is the hard-disk both operating systems are on (verify with 'sudo fdisk -l') you can restore GRUB to the mbr using a live CD terminal:
```
sudo grub-install /dev/sda
```

---

### Post by presence1960 on 2009-11-23
> **aneslin85 said:**
> ***_guys, in my laptop I used Vista, and I installed Ubuntu with wubi._***
and yesterday I did a win7 clean instalation. 
so its overwrite my old bootloader / grub

so, how can I get my ubuntu back ? without instaling it again.
thank you.

You did a clean install so your Ubuntu wubi install is formatted with the rest of your Vista install. Wubi is a file inside the windows filesystem, when windows 7 formatted Vista's partition wubi went with it!

---

### Post by presence1960 on 2009-11-23
> **ptn107 said:**
> If 'sda' is the hard-disk both operating systems are on (verify with 'sudo fdisk -l') you can restore GRUB to the mbr using a live CD terminal:
```
sudo grub-install /dev/sda
```

Ubuntu was installed via wubi, so when the OP did a clean install of windows 7 the Ubuntu wubi install was formatted with the rest of Vista.

---

### Post by aneslin85 on 2009-11-23
thanks for  the replies guys.

my ubuntu partition is in safe.

I just lost my OS selection menu.

i cant fix it via a live CD, because I installed it via wubi.

so how can i fix it?
thanks

---

### Post by phillw on 2009-11-23
As mentioned - if u used wubi - that was installed WITHIN the windows area, it's gone.

post the output of ```
sudo fdisk -l
```

Phill.

---

