---
title: "Infinitely looping update"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by pdusen on 2008-06-25
Hi,

I was trying to install the restricted extras and when it got to the point where it tried to download the flash plugin, it entered into a loop where it just did this repeatedly:
```
http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
  (try: 3) => `./install_flash_player_9_linux.tar.gz'
Connecting to fpdownload.macromedia.com|72.247.74.70|:80... failed: Connection timed out.
Retrying.
```

After a while I killed the update, and now whenever i attempt to update I get this message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

But when I attempt to run sudo dpkg --configure -a, it just goes back into the original loop.

I'm not even interested in continuing the installation at this point, but I need to install some other things like build-essential and this loop is keeping me from continuing. Any suggestions?

---

### Post by Pumalite on 2008-06-25
Try:
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by pdusen on 2008-06-25
It just repeats the error I posted above in the second box.

---

### Post by Pumalite on 2008-06-25
Try:
sudo apt-get remove --purge <packagename>

---

### Post by pdusen on 2008-06-25
Same error.

---

### Post by Pumalite on 2008-06-25
Try:
sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by pdusen on 2008-06-25
> **Pumalite said:**
> Try:
sudo dpkg --remove --force-remove-reinstreq <packagename>

That did it! Thank you very much!

---

### Post by Pumalite on 2008-06-25
You are welcome. Good luck.

---

### Post by Exsecrabilus on 2011-03-04
> **Pumalite said:**
> Try:
sudo dpkg --remove --force-remove-reinstreq <packagename>

OMG I had this problem and you fixed it!! Thanks so much!!!

---

