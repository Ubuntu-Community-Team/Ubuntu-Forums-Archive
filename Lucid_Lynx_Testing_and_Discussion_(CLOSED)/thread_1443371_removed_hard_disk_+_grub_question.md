---
title: "removed hard disk + grub question"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by e1ektrob0y on 2010-03-31
Hi guys. When I installed lucid i installed it on sda and i also had sdb with an old install of i think 8.04. anyway, the other disk had grub on it too and i'm wondering now that i have removed it how can i clean up/update/stabilize grub.

Also on a side note when my machine boots (post 10.04 install) i don't see the old "press esc to enter grub menu" option. Can anyone help me fix this so i can see what kernels are there in grub etc...thanks :)

---

### Post by Barriehie on 2010-03-31
> **e1ektrob0y said:**
> Hi guys. When I installed lucid i installed it on sda and i also had sdb with an old install of i think 8.04. anyway, the other disk had grub on it too and i'm wondering now that i have removed it how can i clean up/update/stabilize grub.

Also on a side note when my machine boots (post 10.04 install) i don't see the old "press esc to enter grub menu" option. Can anyone help me fix this so i can see what kernels are there in grub etc...thanks :)

So grub is on sdb and you want it on sda?

---

### Post by e1ektrob0y on 2010-03-31
nope. grub was on both drives i think. sdb is gone now and grub is installed on the only drive in there which is sda but i think its still looking for sdb when booting which doesnt exist anymore. so i want to clean out grub of all things that arent there anymore. make sense?
and i also want to see grub when the computer boots. when it used to say "grub loading press esc to enter menu". that does not exist anymore...

---

### Post by kansasnoob on 2010-03-31
If you're booting OK you should just be able to run:

```
sudo update-grub
```

Wait for it to say done and that should be it.

With grub2 the Esc key is no longer used to display the boot menu, you must now press the space bar.

This is a pretty great grub2 primer:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by e1ektrob0y on 2010-03-31
thank you very much :)

---

