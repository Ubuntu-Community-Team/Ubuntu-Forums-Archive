---
title: "WLAN driver makefile error"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by Keith_Valin on 2013-11-19
Hello, I've installed LXLE on my laptop.  I found a driver off the Realtek website for linux. I select the file using cd ~/location but when I run "make" through the terminal it gives me this error. ```
make -C /lib/modules/3.2.0-54-generic/build M=/home/keithvalin/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modulesmake: *** /lib/modules/3.2.0-54-generic/build: No such file or directory.  Stop.

make: *** [all] Error 2
``` Can anyone tell me how to get around this?

---

### Post by ubfan1 on 2013-11-19
Try installing the build-essential package.  That should bring in the necessary headers the missing link points to.

---

### Post by steeldriver on 2013-11-19
I don't think build-essential brings in the current kernel headers - that would need the **linux-headers-generic** metapackage I think

I guess we should ask what device you have exactly and how you decided you needed to build the driver from source?

---

### Post by Keith_Valin on 2013-11-19
I have a toshiba satellite L75D-A7823. No clue what you mean by your 2nd statement.

---

### Post by Keith_Valin on 2013-11-20
I installed both packages, same problem, tried rebooting still nothing.  Anyother ideas?

---

### Post by ubfan1 on 2013-11-20
Try the kernel specific packages linux-headers-3.2.0-54-generic and linux-headers-3.2.0-54

---

### Post by Keith_Valin on 2013-11-20
It works!!!!!! Thank you!!!!!!!!!!!!!!!!

---

