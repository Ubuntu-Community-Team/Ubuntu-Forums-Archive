---
title: "Edgy doesn't start"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by Salvatore Di Fazio on 2006-11-11
Hi guys,
I had upgraded my system to the edgy release.
But at the startup the system was stopped in the splash screen.
How can I resolve?

Another question, in the edgy release is there the possibility to install eclipse by apt ?
tnx

---

### Post by igknighted on 2006-11-11
Eclipse should be in the repo's.  Just enable all of them and then type
```
sudo apt-get update
sudo apt-cache search eclipse
sudo apt-get install <whatever package the previous command turned up>
```

Alternatively, after enabling the repo's you could search in any of the GUI package managers if you prefer.

As for the first issue, can you try booting in recovery mode or verbose mode so we can see what kind of errors you are generating?  Many things could cause it to hang during the splash.

---

### Post by Salvatore Di Fazio on 2006-11-11
I wrote the command before the post :)

Anyway the eclipse IDE was not in the packeg list.
Maybe I need another source in my sources.list?
Tnx

---

### Post by Salvatore Di Fazio on 2006-11-11
I resolved.
I ran the system in shell mode, and after I try to lunch Xorg.
After all goes right.

---

