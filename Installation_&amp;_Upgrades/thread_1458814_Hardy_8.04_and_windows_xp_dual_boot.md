---
title: "Hardy 8.04 and windows xp dual boot?"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by mary.ydm on 2010-04-20
I have Hardy Heron 8.04 already on my comp and loving it, however I would also like to have Windows xp on as well, I try to install but get nothing, just directed to the sign in page for linux.  Can someone help please?

---

### Post by jaco223 on 2010-04-20
> **mary.ydm said:**
> I have Hardy Heron 8.04 already on my comp and loving it, however I would also like to have Windows xp on as well, I try to install but get nothing, just directed to the sign in page for linux.  Can someone help please?

Do you have a partition already setup for MS windows?
If not you can create one using GParted, which should be on the
Ubuntu live cd. 

After creating a partition for Windows, you could try your Windows install DVD/CD
to install Windows. I'm not really sure how difficult it is to install Windows from
Ubuntu.
Also you my have to access your system BIOS to tell the computer to boot from the cd rom

[http://www.cyberwalker.com/article/28](http://www.cyberwalker.com/article/28)



Hope this helps.

Jaco

---

### Post by pricetech on 2010-04-20
Short answer:
Set your BIOS to boot to the CD first, or look for a Boot Menu option as your computer boots to temporarily change the boot order to boot the CD first.

Slightly longer answer with a word of caution:
Plan first.  Decide where you want XP to be in terms of how much drive space and make space for it using the Partition Editor in Ubuntu.
Be prepared to repair your MBR after you install XP to make GRUB work again.

---

### Post by jaco223 on 2010-04-20
+1. You can update GRUB with the following:

Open a terminal and type:

```
sudo update-grub
```

---

