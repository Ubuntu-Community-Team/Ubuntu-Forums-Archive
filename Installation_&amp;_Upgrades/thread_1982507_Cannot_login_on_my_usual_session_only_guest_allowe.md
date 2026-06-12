---
title: "Cannot login on my usual session only guest allowed"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by stanlea on 2012-05-18
Ubuntu Studio 12.04 64 bits xfce 
I know that this issue has already been debated, but I can't login to my normal account.

I logged in text mode and deleted .Xauthority, but no way.

It seems that xinit cannot connect to Xserver, like there was another server running, but there is none.

---

### Post by Toz on 2012-05-18
Also have a look at .ICEauthority in your home directory and ensure proper ownership and/or delete that file as well.

Otherwise, Ctrl+Alt+F1, log into the console, and have a look at ~/.xsession-errors for information why it is not allowing you to log in.

---

### Post by stanlea on 2012-05-19
Thank you Toz. 
Watching the content of .xsession.errors showed me the problem : the disk was almost full. Deleting useless stuff made things work well. Thanks again.

---

