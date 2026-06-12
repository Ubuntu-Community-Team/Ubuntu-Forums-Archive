---
title: "Error message every time a system update is performed"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by jomondo45 on 2010-08-01
I'm getting these errors every time a system update is performed. At the end of the process there's a pop-up dialogue with the following message.

E: linux-image-2.6.31-20-generic: subprocess installed post-installation script returned error exit status 127
E: linux-image-2.6.32-21-generic: subprocess installed post-installation script returned error exit status 127
E: linux-image-2.6.32-22-generic: subprocess installed post-installation script returned error exit status 127
E: linux-image-2.6.32-23-generic: subprocess installed post-installation script returned error exit status 127
E: linux-image-2.6.32-24-generic: subprocess installed post-installation script returned error exit status 127
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

If i run a new check for updates, the update manager claims everything is up to date. 
Is there a real install failure? how do i make these errors stop?

I have had these errors since upgrading to lucid lynx a few moths ago

Thanks in advance for any assistance you could provide.

---

### Post by sikander3786 on 2010-08-01
Hi.

Try
```

sudo aptitude clean

```
```

sudo apt-get autoclean

```
```

sudo apt-get update

```
```

sudo apt-get upgrade

```

Regards.

---

### Post by jomondo45 on 2010-08-01
running these commands gave me a clue what was going wrong.. apparently there was a file in /etc/default/ named grub. It had an entry I had added in karmic kola to tweak my radeon graphics card. (radeon.modeset=1) 

this entry was causing the failures as once I removed it leaving that file blank and tried your commands again, the updates finished perfectly!

Thanks for the assistance sikander3786

---

### Post by talking Llama on 2010-08-18
> **sikander3786 said:**
> Hi.

Try
```

sudo aptitude clean

``````

sudo apt-get autoclean

``````

sudo apt-get update

``````

sudo apt-get upgrade

```Regards.


Hey. Thanks. This sorted my problem. Or at least I could see from what these commands returned that I had fiddled around with GRUB and messed something up. After reinstalling GRUB the error messages have gone. Thanks. :D

---

