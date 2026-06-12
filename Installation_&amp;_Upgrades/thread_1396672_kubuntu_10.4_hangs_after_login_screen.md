---
title: "kubuntu 10.4 hangs after login screen"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by abhid on 2010-02-02
I installed kubuntu 10.4 with dual boot. Initially it worked fine but after 2 days it started hanging after the login screen. Pl help

---

### Post by adam814 on 2010-02-02
Are you able to log in to the console?  If you press ALT+F1 you should get a prompt there, does that work at least?

---

### Post by abhid on 2010-02-02
yes i can login from the console

---

### Post by MelDJ on 2010-02-02
try typing kubuntu-desktop and see what happens

---

### Post by adam814 on 2010-02-02
Try this:
```
sudo service kdm restart
```

If you have an internet connection you might want to try this too if that doesn't work:
```
sudo aptitude reinstall kubuntu-desktop
```

---

### Post by lykwydchykyn on 2010-02-02
Did you enable compositing by chance?

What graphics card are you using?

---

