---
title: "Recent Hardy Kernel Update broke bluetooth."
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by edmondt on 2008-05-27
Recently updated to kernel 2.6.24-17-generic on a tx1000 and the built in bluetooth does not seem to detect anymore.

sudo /etc/init.d/bluetooth restart

hcitool dev
Devices:


Any advice?

---

### Post by edmondt on 2008-05-29
Anything? My bluetooth is gone~ I dual boot so I know its working on XP... I found that many are having the same issue, and I have reinstalled bluetooth packages.

Still nothing detected...I want my bluetooth mouse back :(

---

### Post by edmondt on 2008-05-29
Running the following command fixes the bluetooth, but it is gone after the next reboot.

sudo /etc/init.d/udev restart

Is there a way to fix this?

---

### Post by edmondt on 2008-05-29
I've fixed the issue, I posted the fix here: [http://ubuntuforums.org/showpost.php?p=5073794&postcount=1067](http://ubuntuforums.org/showpost.php?p=5073794&postcount=1067)

---

