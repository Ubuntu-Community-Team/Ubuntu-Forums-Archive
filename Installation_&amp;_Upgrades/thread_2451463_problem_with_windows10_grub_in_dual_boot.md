---
title: "problem with windows10 grub in dual boot"
date: 2020-10-05
forum: Installation &amp; Upgrades
---

### Post by shouei on 2020-10-05
Hello,
I just install ubunto 20 in dual boot on my laptop and the windows 10 grub is missing. I tried to fix with boot repair but doesnt help. I share here the link with boot report of the boot repair: [https://paste.ubuntu.com/p/TTYvcgg96p/](https://paste.ubuntu.com/p/TTYvcgg96p/)
theanks!

---

### Post by dragonfly41 on 2020-10-05
In your boot repair report I read  at line 64

**SecureBoot enabled. **

Advice:
Start by turning off SecureBoot in laptop BIOS settings (whatever function button is used since you do not specify laptop make). 

Research the subject in this forum.

---

### Post by ubfan1 on 2020-10-05
The encryption on your Windows parition probably has something to do with this problem.

---

