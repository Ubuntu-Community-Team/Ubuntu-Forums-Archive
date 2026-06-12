---
title: "sudo gdm Stop Error"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by jncocontrol on 2010-12-18
> ** (gdm-binary:8966): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:8966): WARNING **: Could not acquire name; bailing out

I keep getting this error when i try to update my Graphic card.

Any help would be appreciated.

---

### Post by sikander3786 on 2010-12-18
You shouldn't need to stop gdm? How are you trying to update your graphics? Which graphics card is there and any drivers were installed previously?

---

### Post by jncocontrol on 2010-12-18
> **sikander3786 said:**
> You shouldn't need to stop gdm? How are you trying to update your graphics? Which graphics card is there and any drivers were installed previously?

Nvidia 8600GTS, version 183 i believe. But i remember that driver being their since like 2008.

---

### Post by sikander3786 on 2010-12-18
What do you try to achieve after stopping gdm? This commands works for me.

```
sudo service gdm stop
```

Remember, lowercase characters.

---

