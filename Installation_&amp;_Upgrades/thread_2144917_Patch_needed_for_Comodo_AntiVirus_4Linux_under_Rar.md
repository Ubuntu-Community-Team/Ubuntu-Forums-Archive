---
title: "Patch needed for Comodo AntiVirus 4Linux under Raring"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by EAZ on 2013-05-13
It's very easy..




 1. Install Comodo Anti-Virus for Linux (ubuntu or other)


 2. After installation, DO NOT START COMODO (or exit if auto-start)


 3. Download [the patch]("http://www.bondoffamily-net.com/~kinta-chan/techknow/Linux/RedirFS/src/driver.tar") that KINTA-JAPAN made, for the new kernel 3.5 - 3.8 (save under home directory)


 4. Replace current patch under /opt/COMODO/driver.tar with KINTA's patch
```
sudo mv /opt/COMODO/driver.tar /opt/COMODO/driverbkp.tar && sudo cp driver.tar /opt/COMODO/driver.tar
```


 5. Now run the Filesystem post-setup from COMODO
```
 sudo /opt/COMODO/post_setup.sh && sudo /etc/init.d/cmdavd restart
```


Now the error should not longer occur! If not, logout and login or reboot and start CAV!

---

