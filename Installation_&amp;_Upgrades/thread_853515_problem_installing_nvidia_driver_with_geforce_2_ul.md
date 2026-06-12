---
title: "problem installing nvidia driver with geforce 2 ultra"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by kingarthurpt on 2008-07-08
i'm trying to install the driver but now i can't resolv this problem.
I'm attaching the log file.
Can anyone please help me?
Thanks

---

### Post by Pumalite on 2008-07-08
Install build-essential:
sudo aptitude install build-essential
If that is not enough; run this:
sudo apt-get install linux-headers-`uname -r`

---

### Post by kingarthurpt on 2008-07-08
Thank you, It worked out.

---

### Post by Pumalite on 2008-07-08
You are welcome. Good luck!

---

