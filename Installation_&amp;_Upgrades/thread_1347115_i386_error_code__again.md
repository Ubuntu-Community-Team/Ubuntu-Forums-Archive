---
title: "i386 error code ? again"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by cragtom on 2009-12-05
After downloading ubuntu 9.04 and then upgrading to ubuntu 9.10 through the wubi site, I must say I prefer this to the windows vista @@@@ that came installed on the comp but I am having the same problem again it is not letting me install the latest flash 10 for ubuntu saying you have an i386 error someone I know posted a video on x tube and rather than watch it in vista I thought I could watch it in ubuntu as I do not want to take the risk and get this comp infected with any nasties

---

### Post by some-what-Gnu-2-networks on 2009-12-05
are you using a 64-bit OS?

---

### Post by cragtom on 2009-12-06
no even though it is a 64 enabled processor both windows and ubuntu are only 32 bit

---

### Post by some-what-Gnu-2-networks on 2009-12-07
I assume you are trying to install something when this happens. Meaning you are trying to install a64bit plugin on a 32bit OS. Don't you get a 32bit option?

---

### Post by snowpine on 2009-12-07
I recommend opening a terminal and typing:

```
sudo apt-get update && sudo apt-get flashplugin-installer
```

This will automatically find the correct version of the plugin, from the trusted Ubuntu repositories.

If you get any errors, you can cut & paste them exactly here.

---

