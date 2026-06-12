---
title: "update manager help!!!help!!!help!!!!"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by faiz_v10 on 2008-08-11
hi, installed ubuntu like 2 weeks ago and i am loving it and i have no problems on it except for one thing, the update manager.....



im going to guide u to the steps of exactly what happens and the error.





1.first i get the little arrow on the top right corner telling there are updates available, so far every thing is normal, so i click it

2. then the update manager opens and i want to install the updates available, so i click install, 

3. like 3 second after i click install i get this page

[http://s533.photobucket.com/albums/ee335/faiz_v10/?action=view&current=then.png](http://s533.photobucket.com/albums/ee335/faiz_v10/?action=view&current=then.png)

(click this link to see the screenshot, sorry i couldnt figure out how to insert photo on here)

so thanks , and please help me out becase i cant install anything else until i install the updates.


thanks again

---

### Post by snowpine on 2008-08-11
Try opening a terminal (Accessories--Terminal) and typing:

```
sudo dpkg --configure -a
```

then entering your password when prompted. Let us know if that helps!

---

