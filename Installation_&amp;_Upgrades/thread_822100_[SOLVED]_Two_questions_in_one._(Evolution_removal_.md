---
title: "[SOLVED] Two questions in one. (Evolution removal and Icon removal)"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by Indy452 on 2008-06-07
I do not use Evolution mail at all,  and instead of continuing to upgrade it every so often I am wondering if I can remove it safely?
If so, how should I do it?

Also, I tried another browser called Galeon and after decidingf I did'nt like it I decided to remove it. Well Galeon is gone but the icon is still present in my "Internet" category. How do I remove that icon?

Thank you.

Neal

---

### Post by Partyboi2 on 2008-06-07
To remove the Galeon entry, Open up "Main Menu" (System>Pref>Main Menu) and untick or remove it from the list.

Edit: To remove evolution open a terminal and
```
 sudo apt-get remove evolution
```If you want to remove all the config files for it as well add the --purge option
```
sudo apt-get remove --purge evolution
```

---

### Post by Indy452 on 2008-06-08
> **Partyboi2 said:**
> To remove the Galeon entry, Open up "Main Menu" (System>Pref>Main Menu) and untick or remove it from the list.

Edit: To remove evolution open a terminal and
```
 sudo apt-get remove evolution
```If you want to remove all the config files for it as well add the --purge option
```
sudo apt-get remove --purge evolution
```

Thanks, the icon was removed succesfuly. 

Now with the evolution, Is it recommended to remove the config files or just leave them?

Thanks, Neal

---

### Post by Partyboi2 on 2008-06-08
If you plan to use evolution sometime in the future and want to retain your settings just use the remove command but if you are wanting to remove all trace then use the --purge command. You maybe need to remove the 
~/.evolution folder as well after purging.

---

### Post by Indy452 on 2008-06-08
O.K. Thank you!  I chose to leave the config files just in case youknow.

Before I log out, Since I left the config files, will I still be updating the evolution program when updates do arrive?

Neal

---

### Post by Partyboi2 on 2008-06-08
You shouldn't because evolution is no longer installed

---

### Post by Indy452 on 2008-06-08
O.K good to go then.  Thanks for the assistance.

Neal

---

