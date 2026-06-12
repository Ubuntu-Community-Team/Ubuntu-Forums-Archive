---
title: "Installation Freeze"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by t.mil on 2010-05-22
Hi

I am currently running a Dell XPS 630 that is dual-booting Windows 7 and Ubuntu 10.04.  I want to do a clean install of Ubuntu, writing over both current installations.

I have 10.04 on a CD and am able to boot from said CD, but when I reach the first installer screen and select any option other than boot from hard drive, i get a black screen with a blinking cursor.

I tried entering the condition aic7xxx.aic7xxx=no_probe, as suggested for some Dell machines, but i get an error

VFS: Cannot open root device "<NULL>" or unknown block (8,1)

Any help you can give me will be appreciated :)

---

### Post by darkod on 2010-05-22
I haven't heard its Dell specific, but the only other parameter I have seen around is adding nomodeset at the end of the boot line in Try Ubuntu.
If it works, you can install and make it permanent later.

---

### Post by t.mil on 2010-05-23
that didn't work either :(

---

### Post by t.mil on 2010-05-25
bump

---

