---
title: "Cleaning Up Obsolete Packages"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by kingdogbert on 2009-11-16
I just upgraded to Karmic (so far, so good :D). However, when I got to the step where we are offered the option of keeping or removing obsolete packages, I accidentally selected keep. How can I reidentify these obsolete packages and remove them? Thanks

---

### Post by phillw on 2009-11-16
> **kingdogbert said:**
> I just upgraded to Karmic (so far, so good :D). However, when I got to the step where we are offered the option of keeping or removing obsolete packages, I accidentally selected keep. How can I reidentify these obsolete packages and remove them? Thanks

```
*sudo apt*-get autoremove
```

Will tidy things up for you.

Regards,

Phill.

---

### Post by kingdogbert on 2009-11-16
Thanks Phill :)

---

