---
title: "How to absolutely turn off 'swap'?"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by andycivil on 2012-11-02
How can I absolutely turn swap off? Setting 'swappiness' to zero doesn't actually prevent it. I want it so that when I run "top" it actually says "Swap: 0k Total...".

Forgive me if I don't explain why, but I think it might invite argument.

It's looking like the "swapoff -a" command is what I need, but I don't know where to put it, and it would be better to not enable it rather than having it and then disabling it.

---

### Post by darkod on 2012-11-02
Open /etc/fstab for editing with:
gksu gedit /etc/fstab

and simply add # at the start of the line mounting swap. That will comment out (disable) that line. In the future if you want to enable it, remove the #.

Save and close the file. Reboot.

---

### Post by andycivil on 2012-11-02
Worked perfectly, thank you.

---

