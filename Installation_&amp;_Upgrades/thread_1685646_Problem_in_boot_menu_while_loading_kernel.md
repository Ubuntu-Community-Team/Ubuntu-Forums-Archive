---
title: "Problem in boot menu while loading kernel"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by tejendra on 2011-02-11
I have installed a mainline kernel **2.6.38**,parallel with vendor kernel 2.6.35.but boot menu is not appearing and only **2.6.38** kernel is loading at a time,it is not showing the options, if i comment the entries of **2.6.38** kernel from **grub.cfg** file then it is loading the** 2.6.35** kernel automatically.
                                ***Give a solution to let boot benu give me chocie which kenel i want to use.:KS***

---

### Post by amsterdamharu on 2011-02-11
Try to edit the /etc/default/grub with the following commands:
```
sudo nano /etc/default/grub 
```
Check GRUB_HIDDEN_TIMEOUT and make sure it's set to something high like 10
Check GRUB_TIMEOUT and set it to -1, this will wait forever until you select an entry or you can set it to 5 to wait 5 seconds or 0 to boot the default immediately.

After you changed these values press control + x then y then enter

Now execute the following command:
```
sudo update-grub
```

Now you should see a menu.

---

### Post by tejendra on 2011-02-11
thnx buddy..now menu is working fine...thnx fr ur help:):KS

---

