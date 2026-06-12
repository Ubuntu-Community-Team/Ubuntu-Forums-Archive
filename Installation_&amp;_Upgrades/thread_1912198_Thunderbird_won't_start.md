---
title: "Thunderbird won't start"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by sujop on 2012-01-20
I use thunderbird 8.0. Thunderbird does not start when I try to launch it. When I checked resource monitor, it showed the waiting channel as futex_queue_wait_me. Does anyone know the reason for this and how to fis it?

---

### Post by ottosykora on 2012-01-20
> **sujop said:**
> I use thunderbird 8.0. Thunderbird does not start when I try to launch it. When I checked resource monitor, it showed the waiting channel as futex_queue_wait_me. Does anyone know the reason for this and how to fis it?

I would probably try to reinstall it simply and see if the problem persists

---

### Post by ajgreeny on 2012-01-20
Also it is worth starting it in terminal with command ```
thunderbird
```to see if error messages appear.

---

### Post by SeijiSensei on 2012-01-20
Check /home/username/.thunderbird/xxxxxxxx.default/ and see if you have either a "lock" or a ".parentlock" file.  Delete either or both and try again.

---

