---
title: "Minotaur only logs in my account on Xorg"
date: 2023-11-04
forum: Installation &amp; Upgrades
---

### Post by Automat2 on 2023-11-04
Hi,
I have upgraded to Minotaur (23.10) from Lobster (23.04) today. 
Before then, I logged it on 'Ubuntu' -Wayland?- mode. Now, I have to log in on 'Ubuntu on Xorg' because the default 'Ubuntu' mode reverts me to the log in screen after a black screen when I type my password. I am the main admin account on that PC.
However, I asked my son to log in to his account after upgrading and he's able to log in 'Ubuntu' mode.
Do I have to log in 'Xorg' mode from now? Is there any reason I can't log in 'Ubuntu' mode now? Is it possible to change it?
Many thanks.

---

### Post by #&amp;thj^% on 2023-11-04
Just a thought, but have you tried with your user current, and back-up " ~/.config"
```
mv ~/.config ~/.config.bk
```
And try to login under wayland again.

---

### Post by Automat2 on 2023-11-04
It has worked!
I have to reset and reconfigure many things but at least I can log in!
Many thanks. :lol:

---

### Post by #&amp;thj^% on 2023-11-04
My pleasure, enjoy

---

