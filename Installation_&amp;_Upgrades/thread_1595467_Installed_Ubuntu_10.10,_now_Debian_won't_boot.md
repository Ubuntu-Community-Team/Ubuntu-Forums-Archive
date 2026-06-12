---
title: "Installed Ubuntu 10.10, now Debian won't boot"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by geoguy on 2010-10-13
I installed Ubuntu 10.10 yesterday afternoon to give it a go and see what its like. I usually use another debian (sid) though, and its installed on another partition. It was booting fine, but somehow after I installed ubuntu, the boot process wont complete... now when I boot into Debian it jungs hangs/freezes/stops after a partial boot process. And I can't figure out why...all UUIDs in /etc/fstab are correct.

Any ideas?:confused:

Thanks

---

### Post by Rubi1200 on 2010-10-13
Did you run ```
sudo update-grub
``` in the terminal from Ubuntu?

Post the output also.

---

### Post by vorgusa on 2010-10-13
This did not work for me, the only way I can get into Ubuntu 10.10 is to run the install CD and tell it to boot from local disk

---

