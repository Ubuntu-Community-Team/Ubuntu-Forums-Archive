---
title: "Changing GRUB's background"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by bleakcabal on 2005-06-06
Hi I installed Ubuntu yesterday. I ran other Linux distro's before and in the GRUB loading screen I could have a backgroun, instead of the black screen Ubuntu uses. Anyone know how this can be done ?

---

### Post by jerrybme on 2005-06-06
You can install some nice splashcreens with synaptic, do a search for grub and you'll find the package. Then is a simple matter of editing the grub menu. You'll find it in the /boot/grub/ directory. The graphics will be installed to /boot/grub/splashimages/
Add ```
splashimage=(hd0,0)/boot/grub/splashimages/filename.xpm.gz
```
The '(hd0,0)' should reflect which drive you have your ubuntu installed to.

---

### Post by bleakcabal on 2005-06-06
Thanks for the help. I did not find the package you were refering to while searching for grub or splash in Synaptic, but I googled it and found this web-site which contains some usuable images for Ubuntu bootsplash which are quite nice : [http://sleepybuddha.sl.funpic.de/ubuntu/](http://sleepybuddha.sl.funpic.de/ubuntu/)

---

### Post by jerrybme on 2005-06-06
You probably haven't enabled the additional repositories in Synaptic which is why you didn't see the splash images. Nice find on the other splash images  :)

---

### Post by bleakcabal on 2005-06-07
How do you enable these ?

---

### Post by Gtaylor on 2005-06-07
Good find there! Maybe this should be added to Ubuntuguide.

---

