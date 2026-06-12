---
title: "Ubuntu vs Zorin Grub Menu"
date: 2016-03-25
forum: Installation &amp; Upgrades
---

### Post by O)9(yo&amp;# on 2016-03-25
I recently installed Ubuntu on a drive that has Zorin on it. As expected, Ubuntu's Grub took precedence. I would boot the computer and Ubuntu's Grub appeared, where I could choose it or Zorin. However, after updating Zorin, I now get the Zorin Grub when booting up. Somehow Zorin took control of Grub, even though Ubuntu was the last OS installed. Any way to fix this?

---

### Post by grahammechanical on 2016-03-25
This happens if there is an update to the kernel or an update to grub itself. Is there only one hard disk? sda?

Load Ubuntu. Open a terminal and run these 2 commands

```
sudo update-grub
sudo grub-install /dev/sda
```

That should put Ubuntu back in change.

Regards

---

### Post by O)9(yo&amp;# on 2016-03-25
Thanks, that worked! I actually had it in my Linux cheat sheet, but didn't know it would solve this. Or knew and forgot? By the way, does it matter in what order you run the commands?

---

### Post by O)9(yo&amp;# on 2016-03-26
You may mark this as solved.

---

### Post by Bucky Ball on 2016-03-26
> **michael_diemer said:**
> You may mark this as solved.

Actually, you may. ;) See the first link in my signature below. 

Yes, the commands must be in that order.

---

### Post by O)9(yo&amp;# on 2016-03-26
Thanks again and I'll mark as solved.

---

