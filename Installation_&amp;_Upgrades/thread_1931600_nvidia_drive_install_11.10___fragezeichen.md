---
title: "nvidia drive install 11.10   fragezeichen"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by fidas on 2012-02-25
hi  forum 

i am trying dto update nvidia driver for 11.10 and when try to stop light dm i get  this message : 


root@brasil:~# sudo lightdm stop
Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?

  i am new  here so  please have some understanding.

thx  forum in advance :confused::popcorn::confused:

---

### Post by MAFoElffen on 2012-02-25
> **fidas said:**
> hi  forum 

i am trying dto update nvidia driver for 11.10 and when try to stop light dm i get  this message : 


root@brasil:~# sudo lightdm stop
Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?

  i am new  here so  please have some understanding.

thx  forum in advance :confused::popcorn::confused:
The desktop manager is set as a "service" now (since v11.04)

//Der Desktop Manager wird als eine "Dienstleistung" jetzt (seit v11.04) setzen//
```

sudo service lightdm stop

```

---

### Post by fidas on 2012-02-25
aha  looks like it  

thx for info

---

