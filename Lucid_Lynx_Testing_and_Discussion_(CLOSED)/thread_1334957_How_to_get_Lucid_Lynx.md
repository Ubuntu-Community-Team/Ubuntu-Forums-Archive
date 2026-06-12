---
title: "How to get Lucid Lynx"
date: 2009-11-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by shortyg33 on 2009-11-23
hi guys I just did a fresh install of 9.10 how can i get Lucid installed i would like to try it out.

can i upgrade or is there an iso yet ?

thanks for your help

---

### Post by shortyg33 on 2009-11-23
sorry i found it thanks anyway

---

### Post by nitstorm on 2009-11-23
where???

---

### Post by slakkie on 2009-11-23
[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

I don't think that update-manager knows about lucid, so you would need to do it the debian way. Best of luck.

---

### Post by Gina on 2009-11-23
I don't think you can use update-manager either.  I used the daily live ISOs to install Lucid into a fresh partition.

---

### Post by ranch hand on 2009-11-23
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by VMC on 2009-11-23
> **ranch hand said:**
> [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Thanks ranch hand. On the day alpha1 comes out ~12/3, the daily-live on that same day will be the same, correct?

---

### Post by jppr on 2009-11-23
[https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)   you can see when alpha1 comes out ;) and daily-live is same.

there is all daily-build systems... [http://cdimage.ubuntu.com/ ]("http://cdimage.ubuntu.com/")

---

### Post by nitstorm on 2009-11-23
is there a torrent for now?

---

### Post by ranch hand on 2009-11-23
I haven't seen one yet.

---

### Post by ronacc on 2009-11-24
if you want to just upgrade from a karmic install , edit your /etc/apt/sources.list to replace all instances of karmic with lucid . Then in a terminal ```
 sudo apt-get update 
``` then when that finishes ```
 sudo apt-get upgrade 
``` then ```
 sudo apt-get dist-upgrade 
``` or after editing your sources.list open synaptic and hit "reload"  after that finishes hit "mark all upgrades" then "apply" .

---

