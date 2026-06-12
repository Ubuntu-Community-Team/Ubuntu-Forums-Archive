---
title: "/home passkey recovery"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by ffixcollector on 2010-07-21
I have encrypted my home directory during a fresh install, after I booted up for the first time is asked me to write down my /home passkey paraphrase for emergency recovery. I chose to do it later. Now I cant find the command to recover the passkey. Does anyone know how to do this?

---

### Post by quixote on 2010-07-23
If you don't have a lot in that /home directory yet, how about just making yourself a new home directory (and this time writing down the passkey :D), and then, as sudo, deleting the old home directory?

I realize that's a workaround, not a solution, but it might be the simplest way.

---

### Post by lechien73 on 2010-07-23
I think the command you're looking for is:

```
ecryptfs-unwrap-passphrase
```

Then you put in your user password at the prompt.

---

### Post by ffixcollector on 2010-07-27
Thats It! Thank you that is the command I was looking for.

---

