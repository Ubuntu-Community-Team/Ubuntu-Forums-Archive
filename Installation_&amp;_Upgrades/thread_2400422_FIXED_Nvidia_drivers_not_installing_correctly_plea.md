---
title: "FIXED* Nvidia drivers not installing correctly please help."
date: 2018-09-05
forum: Installation &amp; Upgrades
---

### Post by bunchie on 2018-09-05
FIXED*
(im using Ubuntu 18.04).in software and updates it says i have nvidia 390 drivers but it also says i have no proprietary drivers either. it wont let me change which driver i what either, when i try to select a different one it just switches back. in system setting under about it says my graphics are NV117 (i have a GTX 750ti) now im assuming that mean nividia drivers 117 but i could be wrong. iv tried looking up this issue and found nothing, iv tried installations but im not fully understating of what is happaing over the error of unmet dependency and no way to fix then, since when i do the sudo fix command it give me more unmet dependency.
[ATTACH=CONFIG]280995[/ATTACH][ATTACH=CONFIG]280994[/ATTACH][ATTACH=CONFIG]280996[/ATTACH][ATTACH=CONFIG]280997[/ATTACH][ATTACH=CONFIG]280998[/ATTACH]

---

### Post by lordfrikk on 2018-09-06
Have you tried removing the old package first?

---

### Post by bunchie on 2018-09-06
with the pune command, sadly yes.

---

### Post by bunchie on 2018-09-06
i tried to pure nvidia for a fourth time and got more unmet dependencys, and this is the same errors for the other drivers i tried to install.

---

### Post by Bashing-om on 2018-09-06
bunchie; Hello - 

Show us the errors by posting the outputs - Between code tags - of terminal commands:
```

sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

see what it takes to put the package manager in a happy state .

[INDENT]If the package manager is not happy
[INDENT][INDENT][INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bunchie on 2018-09-06
ill just reinstall

---

### Post by Bashing-om on 2018-09-06
> **bunchie said:**
> ill just reinstall

Ahwww yes, that nuclear solution that always works :) .. but we learn little with that option .

[INDENT]easy way out
[/INDENT]

---

### Post by oldos2er on 2018-09-06
> **bunchie said:**
> ill just reinstall

And when this issue comes up again, then what? Despite the fact that it says "open source", you are using the correct drivers.

---

### Post by bunchie on 2018-09-07
it worked, the software and update finally let me pick a proprietary driver, thanks for the help and ideas tho.

---

### Post by Bashing-om on 2018-09-07
bunchie; Outstanding :)


[INDENT]where there us a will, there is a way[/INDENT]

---

