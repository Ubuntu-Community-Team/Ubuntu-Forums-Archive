---
title: "Plymouth theme help"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by AZorin on 2010-04-26
Hello, I've recently created a Plymouth theme that is based on the  regular Ubuntu 10.04 one, I only changed the colours and graphics. When I  set it, it only shows the theme I have made during shutdown. When I  start up my computer it shows the regular Ubuntu one.
Is there any way to show the same theme for both startup and shutdown?

Thanks in advance
AZorin

---

### Post by jpeddicord on 2010-04-26
```
sudo update-initramfs -u
``` should fix it, I think. The boot image stores a copy of Plymouth and that is what you were seeing.

---

### Post by AZorin on 2010-04-27
Thanks, it worked :)

---

