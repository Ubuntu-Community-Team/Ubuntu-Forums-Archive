---
title: "getting flash to work?"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by shultzjr on 2010-02-14
I downloaded and extracted libflashplayer.so in Ubuntu 9.10 DT 64 bt.  Now where do I put it to make it work?

thanks,
charles......

---

### Post by Satoru-san on 2010-02-14
My brother uses 64 bit kubuntu. All we had to do was uncomment the restriced repositories from the sources.list then apt-get install kubuntu-restricted-extras. This will install flash, 64 bit flash for that matter, you dont need to do anything special.

---

### Post by shultzjr on 2010-02-14
I am using ubuntu 9.10 DT 64bit.  the sources.list file is set but I couldn't figure out the exact command to do the upgrades.  any ideas?

thanks....

---

### Post by Soul-Sing on 2010-02-14
download 64 bit version: [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)
unpack the tar in lets say: 64 flash folder in /home
copy [COLOR="Red"]libflashplayer.so[/COLOR] in ./mozilla/plugin map
chromium==> usr/lib chromium/plugi nmap

---

### Post by oldos2er on 2010-02-14
AFAIK the restricted-extras packages still install 32-bit flash with nspluginwrapper.

---

### Post by Soul-Sing on 2010-02-14
> **oldos2er said:**
> AFAIK the restricted-extras packages still install 32-bit flash with nspluginwrapper.

indeed

---

