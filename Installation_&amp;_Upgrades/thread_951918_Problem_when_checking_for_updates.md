---
title: "Problem when checking for updates"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by anncabana on 2008-10-18
Two days ago, my computer ran updates, and that's when problems started occurring. The other day it claimed I had new updates, but now it says there was a problem when checking for them.  I've tried running updates in the terminal, but it just responded with "segmentation faulty tree 50%".  How do I get these updates to run and get my computer back to normal?

---

### Post by forger on 2008-10-18
type this in Applications > Accessories > Terminal:
```

uname -a
lsb_release -a
sudo apt-get -f install
sudo apt-get update

```

Post back with the full output :)

---

### Post by anncabana on 2008-10-19
I tried what you said and it said no LSB modules are available, the segmentation faulty tree still only went to 50%, and even after running sudo apt-get update, it didn't fix anything. :( It won't let me run any updates without randomly closing on its own. Any other ideas??

---

### Post by Partyboi2 on 2008-10-19
Try removing  the /var/cache/apt/*.bin files or rename them to file.bin.old (change file to actual name) then run ```
sudo apt-get update 
```afterwards, this should regenerate the files.

---

### Post by anncabana on 2008-10-19
Where do I find these files that need to be changed? I'm completely clueless when it comes to Ubuntu!

---

### Post by anncabana on 2008-10-19
Where do I find these files that need to be changed? I'm completely clueless when it comes to Ubuntu!

---

### Post by Partyboi2 on 2008-10-20
> **anncabana said:**
> Where do I find these files that need to be changed? I'm completely clueless when it comes to Ubuntu!
Press Alt+F2 and in the box that opens type
```
gksu nautilus /var/cache/apt 
``` you will see a couple of files that end in .bin right click on them and  rename them to something else eg .file.bin to file.bin.old. After you have made the changes open a terminal (Applications>Accessories>Terminal) and type ```
sudo apt-get update
```

---

### Post by anncabana on 2008-10-21
Thank you so much! I was able to get my updates after renaming those files.

---

### Post by Partyboi2 on 2008-10-21
> **anncabana said:**
> Thank you so much! I was able to get my updates after renaming those files.
Your welcome :)

---

