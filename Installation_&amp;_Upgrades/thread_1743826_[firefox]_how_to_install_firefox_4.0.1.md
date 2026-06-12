---
title: "[firefox] how to install firefox 4.0.1?"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by ssek on 2011-04-29
Hello I installed ubuntu 11.04
but the default installed firefox is 4.0 of canonical

how do we upgrade to 4.0.1???

Someone can tell me the terminal command for upgrading properly?

---

### Post by cazador31 on 2011-04-29
> **ssek said:**
> Hello I installed ubuntu 11.04
but the default installed firefox is 4.0 of canonical

how do we upgrade to 4.0.1???

This is how I upgraded to 4.0.1

Someone can tell me the terminal command for upgrading properly?

sudo add-apt-repository ppa:mozillateam/firefox-stable
 
sudo apt-get update
 
sudo apt-get upgrade

---

### Post by Silmeron on 2011-04-30
That unfortunately doesn't work (yet) presumably because there's no 11.04 channel for Firefox up yet (if you try that, you'll get 404 errors.)

---

