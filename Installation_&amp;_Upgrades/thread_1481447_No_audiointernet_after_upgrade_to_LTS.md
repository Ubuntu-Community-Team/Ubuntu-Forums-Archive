---
title: "No audio/internet after upgrade to LTS"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by WOOHOOHOO on 2010-05-12
Hi,

Upgraded 5 days ago, just noticed no audio or internet icon on the panel (internet works tho)..

I've tried different things i/'ve found on the forum, including editing thingd in the preferences>startup applications part, nothing has worked. I've an old laptop and not sure what info you need. Audio worked fine before the upgrade..

Thanks in advance.

---

### Post by Iowan on 2010-05-12
> **WOOHOOHOO said:**
> Upgraded 5 days ago, just noticed no audio or internet icon on the panel (internet works tho)..So...
Internet works - just no Network Manager icon on the panel? (Re)installing a "Notification Area" *might* get NM back.

---

### Post by WOOHOOHOO on 2010-05-13
could you talk me through that please.

Anyone any ideas about how to get audio qworking again please?

thanks!

---

### Post by raygj on 2010-05-13
> **WOOHOOHOO said:**
> could you talk me through that please.

Anyone any ideas about how to get audio qworking again please?

thanks!

give this a go 
[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script")

then reboot computer

---

### Post by WOOHOOHOO on 2010-05-14
i did find that post before, its what made my computer worse. I followed these steps, now i cant get on internet either and have no sound still.

1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.23-2.tar
4. sudo ./AlsaUpgrade-1.0.23-2.sh -d
5. sudo ./AlsaUpgrade-1.0.23-2.sh -c
6. sudo ./AlsaUpgrade-1.0.23-2.sh -i
7. sudo shutdown -r 0

---

