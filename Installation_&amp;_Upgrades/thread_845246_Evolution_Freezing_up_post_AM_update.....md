---
title: "Evolution Freezing up post AM update...."
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by bhathco on 2008-06-30
Hey all,
I got an update notification this AM, Base-Files? Anyway, let it go through, and now Evolution is freezing up when I try to reply to someones message. I've done some digging, and all I can seem to come up with is in the auth.log, I get: 

```
Jun 30 10:27:52 bahbuntu gnome-keyring-daemon[6337]: couldn't write 143 bytes to client: Broken pipe
```

Could this be coincidence, or is it something else entirely?

Thanks!

---

### Post by bhathco on 2008-06-30
turns out the global catalog setting within Evolution got erased somehow. I put it back and all was well.  Hhmmm...

---

