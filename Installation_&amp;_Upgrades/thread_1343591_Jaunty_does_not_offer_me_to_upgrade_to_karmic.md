---
title: "Jaunty does not offer me to upgrade to karmic"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by owg on 2009-12-02
Hello to everybody.

Trying to upgrade to 9.10 on an Acer Aspire One.

I installed jaunty a couple months ago for a friend of mine, never updated/upgraded 'till tonight  that i run an apt-get update && apt-get upgrade, upgraded several things (like kernel 2.6.28-16) fine, but afterwards did not upgrade with an apt-get dist-upgrade, not even GUI tells me that is avaliable.

Tried apt-get clean, autoclean, but nothing karmic just wont show up. Any ideas on that?

---

### Post by NCLI on 2009-12-02
> **owg said:**
> Hello to everybody.

Trying to upgrade to 9.10 on an Acer Aspire One.

I installed jaunty a couple months ago for a friend of mine, never updated/upgraded 'till tonight  that i run an apt-get update && apt-get upgrade, upgraded several things (like kernel 2.6.28-16) fine, but afterwards did not upgrade with an apt-get dist-upgrade, not even GUI tells me that is avaliable.

Tried apt-get clean, autoclean, but nothing karmic just wont show up. Any ideas on that?

Try running: "sudo apt-get update && update-manager -c"

If that doesn't work, try running "sudo update-manager -c"

---

### Post by owg on 2009-12-02
> **NCLI said:**
> Try running: "sudo apt-get update && update-manager -c"

If that doesn't work, try running "sudo update-manager -c"

The first one did not worked, but "sudo update-manager -c" did the trick.

Thanks a lot.

---

### Post by mkvnmtr on 2009-12-02
You might check on software sources which upgrade is enabled. If it is for long term support you will not be offered an upgrade . If you change it to normal releases you should be offered each upgrade.

---

