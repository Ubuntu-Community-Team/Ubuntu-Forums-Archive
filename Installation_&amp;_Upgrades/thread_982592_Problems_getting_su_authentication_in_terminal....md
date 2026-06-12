---
title: "Problems getting su authentication in terminal..."
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Koil_1 on 2008-11-14
I'm using Ubuntu 8.04 Hardy and having serious problems getting into super user mode from the console. If there's an administrator setting I'm missing somebody please fill me in. I can't install anything from a make file until this gets fixed. It's really frustrating to say the least.

---

### Post by littlebat on 2008-11-14
You can't "su" to root in ubuntu commonly, just type "sudo yourcommand" to perform root tasks.
If you like stay at "root" account a while, just type "sudo -s". Enjoy.

---

### Post by inobe on 2008-11-14
i think this may help you, i am not sure

in terminal do

```
sudo apt-get install nautilus-gksu nautilus-open-terminal
```

it will allow you to right click a file and open as admin, also able you to click anywhere in nautilis and open terminal.

---

### Post by Koil_1 on 2009-01-23
This helped a lot. Thank you.

---

