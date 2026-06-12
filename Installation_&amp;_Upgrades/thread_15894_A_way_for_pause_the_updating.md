---
title: "A way for pause the updating?"
date: 2005-02-17
forum: Installation &amp; Upgrades
---

### Post by ZuLuuuuuu on 2005-02-17
Hi, I typed  $ sudo apt-get upgrade and it's processing now. But I must shut down the computer in 1 hour's time. Is there a way to pause the upgrading and then resume?

---

### Post by iceman.c3k on 2005-02-17
You can stop the downloading of packages or updating of the system, by pressing "Ctrl+C" and stopping the program. This will stop the program completely. The next time you try the same command, apt-get will resume downloading from the point where it stopped last time.

---

### Post by ZuLuuuuuu on 2005-02-17
[QUOTE=iceman.c3k]You can stop the downloading of packages or updating of the system, by pressing "Ctrl+C" and stopping the program. This will stop the program completely. The next time you try the same command, apt-get will resume downloading from the point where it stopped last time.[/QUOTE]
 Thanks :)

---

