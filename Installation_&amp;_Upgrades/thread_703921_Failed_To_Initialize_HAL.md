---
title: "Failed To Initialize HAL"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by DrSunnysock on 2008-02-21
I installed Ubuntu 7.04 with the latest stable release of Wubi.


All worked well until I upgraded to 7.10 using Ubuntu's built in upgrader. Upon rebooting the computer after the upgrade process finished, an error message popped up that said "Failed To Initilize HAL."

I am also unable to connect to the internet. My USB internet dealie which connects to a network isn't recognized and as soon as I open the device manager it closes itself. I was able to connect to the internet before the upgrade.

This is happening on a Sony Vaio desktop computer.

---

### Post by Partyboi2 on 2008-02-21
can you open a terminal and try
```
sudo /usr/lib/hal/hald-generate-fdi-cache

```

---

### Post by DrSunnysock on 2008-02-21
> **Partyboi2 said:**
> can you open a terminal and try
```
sudo /usr/lib/hal/hald-generate-fdi-cache

```

I love you.

---

### Post by itsjustarumour on 2008-02-22
Alas, that fix didn't work for me.

All I'd done was install a newer version of AWN using this how-to here:

[http://ubuntuforums.org/showthread.php?t=385981&highlight=AWN](http://ubuntuforums.org/showthread.php?t=385981&highlight=AWN)

Rebooted my machine to check AWN would start up OK, and got the HAL error message and no network connection - seems like Network  Mangler had just ditched the settings for both my Ethernet and Wireless connections.  Also seems to have broken Google Desktop too.

Seems like some other people have been getting the same message, theres another open thread on this at [http://ubuntuforums.org/showthread.php?t=578952&highlight=HAL+failed](http://ubuntuforums.org/showthread.php?t=578952&highlight=HAL+failed)

I'll pop over there and have a look :-)

---

