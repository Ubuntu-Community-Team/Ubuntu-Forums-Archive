---
title: "Cannot boot live CD"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by shaheel16 on 2010-05-23
I am trying to boot the latest Ubuntu/Kubuntu 10.04 Lucid Lynx but im facing the same problem. The scrolling dots appear but then when its supposed to load X, no display on my monitor:confused:.. My monitor shows no signal.

I am getting this bug on ubuntu, kubuntu and even linux mint which is a spinoff of ubuntu. Is there no way for me to boot the live cd using safe graphics mode or something? Same error when trying to install using wubi.

My PC Specs:

Intel Dual Core E5200
2 GB RAM
Nvidia 9400 GT 512 Mb
250 GB HD

currently dual booting Windows XP and 7 ..

Any suggestions idea most welcome.. :confused::confused::confused::confused:

---

### Post by Tkdboy on 2010-05-23
can u load live cd and work with it?

---

### Post by shaheel16 on 2010-05-23
well.. 9.10 karmic koala and previous 9.04 are booting well. Only problem with new release.. I dont know what is bugging.. mayB my monitor?? its a viewsonic 19" so normally resolution high 1140* 900 ..

---

### Post by Tkdboy on 2010-05-23
did u update the previews version or u are trying too boot 10.04 from live cd?

---

### Post by Rubi1200 on 2010-05-23
You can try this workaround (has helped a number of people already):

[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

Let us know if it helps.

By the way,

> I am getting this bug on ubuntu, kubuntu and even linux mint which is a spinoff of ubuntu. Is there no way for me to boot the live cd using safe graphics mode or something? Same error when trying to install using wubi.If the workaround is successful for you it will also work on the other versions you mentioned. Just so you know, Wubi can be problematic; best to avoid it and use LiveCD versions instead.

The reason you cannot boot with the other versions is because they all use the same kernel. Also, safe graphics mode (or compatibility mode as it is also called) was removed from 10.04 as a menu option.

---

