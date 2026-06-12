---
title: "Should I switch kernel?"
date: 2005-02-26
forum: Installation &amp; Upgrades
---

### Post by oVerCaffeinated on 2005-02-26
I did **sudo apt-get install linux-686** on an AMD XP machine. I'm thinking I really should've done **sudo apt-get install linux-k7**. If I do it right now will it stuff up anything? Am I going to get anything good out of changing to the K7 kernel, like better speed or stability?

---

### Post by Leif on 2005-02-26
No, it won't give you any problems. Changing to k7 should give you better performance, so I definitely recommend it. And for the very minute chance of something going wrong, unless you remove the old kernel, it will still be available as a choice in grub during bootup, so you can always go back to it.

---

### Post by oVerCaffeinated on 2005-02-26
Rebooted and everythings OK [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img] Thanks for the help.

---

### Post by jdong on 2005-02-26
Use it if you'd like. It, theoretically, should be faster. However, I've never seen any sort of benchmark PROVING that it's faster to use an optimized kernel, nor have I ever noticed optimizing kernels causing any kind of boost on my desktop.

Voodoo kernel optimizing is great, though :D

---

