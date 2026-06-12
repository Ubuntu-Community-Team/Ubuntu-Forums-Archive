---
title: "pci error message on clean install"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by coderunner on 2007-04-22
I just finished a clean install of feisty after an upgrade from edgy didn't turn out too well.  Now when I boot into ubuntu, I always get this error message displayed in the middle of the ubuntu loading bar logo:

[    0.113693] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0

So far everything seems to be ok, however, I'd like to fix it if it may end up destroying my installation later after I have alot of work saved in my linux installation.  I'm not sure which PCI device its having problems with, but does it look like a serious problem?

Thanks

---

### Post by nabla on 2007-04-24
I get another error failed to allocate I/O resource. Haven't seen any noticeable problem while running. I'll check if there's a bug report on launch pad sometime tomorrow.

---

### Post by creamcheeze77 on 2007-04-25
googling this, it seems to be pretty harmless.  i also get this error, and taking out the graphics card gets rid of it.  i'm assuming it's some sort of driver problem.  not sure if this helps any..

---

### Post by coderunner on 2007-04-25
Thanks, I didn't even think to google it because I thought the Id's might be specific to my machine.  But if its just an issue with drivers for a pci device, then it doesn't sound like something to worry too much about.

---

