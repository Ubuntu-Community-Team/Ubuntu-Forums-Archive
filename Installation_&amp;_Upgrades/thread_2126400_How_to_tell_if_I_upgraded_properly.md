---
title: "How to tell if I upgraded properly"
date: 2013-03-17
forum: Installation &amp; Upgrades
---

### Post by toad3000 on 2013-03-17
Hi I Just updated to ubuntu 12.04 from 10 and the strange thing is that the window that says you have been upgraded didn't show up when I restarted my computer. And the other strange thing is that when I Open a window the close minimize and maximize icons are the same ones from ubuntu 10. When I check system details it says 12.04. But here and there it looks like 10. Thanks.

---

### Post by fantab on 2013-03-17
You should give more info then "But here and there it looks like 10". Ubuntu uses AMBIANCE theme as its default theme since long before Ubuntu 10. So windows theme will appear to be same but for some minor changes, looks wise.

```
$ sudo apt-get update
```

See if any errors show up.

Try removing the hidden user configuration folders/files (dot files/folders) from your /home directory for the applications you think 12.04 theme is not working properly, and restart applications. Be warned that by doing so you will lose any applied settings/preferences you haave for that application.

Good Luck...

---

