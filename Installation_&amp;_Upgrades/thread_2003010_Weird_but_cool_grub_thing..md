---
title: "Weird but cool grub thing."
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by jso2897 on 2012-06-13
I have a HP Pavillion PC with an AMD chip that I have two hard drives installed in. One of them I loaded with Win 7, the other with Ubuntu 12.04.
I was just going into the boot menu when I powered up and selecting whichever drive I wanted - if I didn't, it would default to the drive with Ubuntu, just because it listed first on the boot menu.
This was like that for about a week, and then, this morning, when I powered up, a GRUB menu popped up! Now I can boot up just as if I had done a conventinal dual boot - GRUB somehow figured it out and confifured it without my doing anything.
I'm not complaining - it's cool - but I'm a little puzzled.:lolflag:

---

### Post by wilee-nilee on 2012-06-13
You probably had a grub upgrade, which run a update, you could of had the same with this command run in Ubuntu.
```
sudo update-grub
```

Grub 2 has app called os-prober it find other OS's

---

### Post by drs305 on 2012-06-13
I believe there was a kernel update within the past 24 hours. When the kernel is updated one of the results is the automatic running of "update-grub". That is probably what triggered it.

---

### Post by jso2897 on 2012-06-13
Bingo. I upgraded just before it happened - and there was a kernel upgrade. That's it. Cool.:p

---

### Post by jso2897 on 2012-06-13
Although I'm not sure why I'm so happy - I just basically demonstrated thatsomething called "GRUB" is smarter than I am.

---

