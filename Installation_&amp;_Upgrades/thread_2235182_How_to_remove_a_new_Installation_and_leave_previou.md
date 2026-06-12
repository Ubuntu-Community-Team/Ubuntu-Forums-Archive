---
title: "How to remove a new Installation and leave previous one?"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by Arius123 on 2014-07-19
I have now in grub: 

(a) Ubuntu (New, which is responsible for grub)
(b) Ubunutu (Previous installation)
(c) Windows 8 

How i can remove (a) from grub AND ALSO delete partition where it has been installed?

Thank you!

---

### Post by Vladlenin5000 on 2014-07-19
Hi, welcome.

Assuming there are no other problems it should be as easy as booting (b), then use a tool like GParted to remove the partition where (a) is installed and finish with an update to GRUB: ```
sudo update-grub
```

---

### Post by grahammechanical on 2014-07-19
You may also need to run

```
sudo grub-install /dev/sda
```

Because the new install would have installed its Grub into sda. You are at the moment loading from the Grub of the new installation (a). These two commands run from the previous installation (b) will together change which Grub is controlling the boot menu.

Regards.

---

### Post by Arius123 on 2014-07-19
Thank you. 
(First, have switched grub, and then the rest... )

---

