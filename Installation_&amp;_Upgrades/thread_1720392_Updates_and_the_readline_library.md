---
title: "Updates and the readline library"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by Mila on 2011-04-03
Every time I get updates via the update manager, the file libreadline.so.6 gets reinstalled in my /usr/local/lib/ folder. This file breaks gpg (or, at least, it does on my computer), and to fix it I have to download the readline source, compile, and manually install in the /usr/local/lib folder. (Because if I don't I can't get updates what with gpg not working right.)

This is understandably tedious. Is there any way to tell ubuntu "hey, I have readline already, please don't try to install any other versions of it, or rename the existing one?"

(Alternatively, if I install a different version of libreadline, eg. 6.2 which is the latest stable build, I still need to go back, delete libreadline.so.6, and re-chmod libreadline.so.6.2 to 777. Which is also aggravating.)

Thanks.

Mila

---

### Post by Mila on 2011-04-12
Bump. 

This happens every time I upgrade. Even if I compile a version of libreadline and then stick it in /usr/local/lib and name it libreadline.so.6, whenever I try to upgrade that file will be *overwritten* with the non-functioning version of libreadline.

Anybody have some way of stopping this?

---

