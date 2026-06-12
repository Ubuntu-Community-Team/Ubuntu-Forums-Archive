---
title: "Wubi install dell inspiron 1525 issues"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by Pedricko on 2010-04-08
Hi there.

I used wubi to install 9.10 on my dell inspiron 1525.

I had a problem with not being able to get wireless working, and found out that I had to activate the Broadcom STA driver which lead to a crash. Now I've rebooted, everytime I try to install I get 'SystemError() InstallArchives' or the authenticate box hangs.

Is there another way to install these drivers?

---

### Post by leorolla on 2010-04-13
Could you show us the ouput of
```
lspci
```

And if you can get wired connection to update and upgrade your install, it may work just fine after that.

---

