---
title: "Ubuntu upgrade 18.04 (from 16.04) smbd and nmbd services failed"
date: 2018-06-25
forum: Installation &amp; Upgrades
---

### Post by zachalexy on 2018-06-25
Hi, I upgraded from 16.04 to 18.04. Reactivated/installed most repo's, did a lot of tweaking, ... now quite happy with 18.04 (on Unity :-)). I ran the command "systemctl list-units --type service" and found that three services are not running. 1. smbd, 2. nmbd and 3. ureadahead. I guess the samba services fail since 18.04 doesn't allow guest accounts anymore? The ureadahead service I can't explain. I'm also running preload and happy with that (if any parallel?).

Who can help with explanation? Like to keep a clean and all-up OS.

Regards, Zach

---

