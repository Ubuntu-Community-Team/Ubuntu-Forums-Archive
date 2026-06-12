---
title: "Disabled Unity in compizconfig, now menu bar is gone"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by jewely on 2011-05-02
I have Ubuntu 11.04. I wanted to disable Unity in CompizConfig, thinking it would revert to the menu style from previous versions of Ubuntu, but now the menu bars are gone and I can't do anything. I can only see the desktop and the files on it. 

Does anyone know how to fix this? :confused:

---

### Post by mikewhatever on 2011-05-02
Select the 'Ubuntu Classic' option at the login screen. That should load the old Gnome2 interface + compiz.

---

### Post by jewely on 2011-05-02
I have no login screen, it goes straight to the desktop. I can't turn that option on either.

---

### Post by mikewhatever on 2011-05-02
Hit ctrl+alt+f1, that should drop you to the console login prompt. Login, then type:
```
sudo service gdm restart
```

...that should bring you back to the login screen.

---

### Post by echo6 on 2011-05-02
From a console terminal try unity --reset

---

### Post by jewely on 2011-05-02
Thanks guys, that fixed it

---

### Post by mike_crossgreen on 2011-05-03
Hey yeah had same problem, was only able to get to this because i had a keyboard shortcut for loading firefox :-) the "unity --reset" seems to be working though it's still in the process of doing something i'm not quite sure.. 

Thankyou! :)

---

### Post by maembe on 2011-05-03
How long should it take to do unity --reset?
I feel like its been running a long time for me and hasn't changed from "Setting Update 
toggle_window_shaded_key" in awhile.

---

