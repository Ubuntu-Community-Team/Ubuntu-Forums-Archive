---
title: "How to not update graphics driver."
date: 2015-07-28
forum: Installation &amp; Upgrades
---

### Post by Chase_Preuninger on 2015-07-28
I recently installed cuda along with the nvidia driver which came with it.  I then installed updated for ubuntu and when I rebooted the graphics were broken and I could not log in.  I think ubuntu may have tried to update the original graphics driver.  How do I disable updates of the graphics driver?

---

### Post by dino99 on 2015-07-28
from a terminal, run:

> sudo apt-mark hold myfavoritepackage

select the exact driver name ,in your case, you want to be not upgraded when a newer version come.
to get a newer version (if you change your mind) then use 'dist-upgrade'

---

### Post by monkeybrain20122 on 2015-07-28
AFAIK Ubuntu doesn't upgrade the Nvidia driver unless you install from ppa. Sounds like it has upgraded the kernel. If you install the driver manually from Nvida to use CUDA (as oppose to repo or ppa) then you would have to rebuild the driver when there is a kernel update.  You can pin the kernel, but a better way is probably to grab the latest kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) then build your driver against it, that way you won't be affected by any Ubuntu kernel upgrade because your version supersedes all Ubuntu kernel upgrades and you choose when you want to upgrade (and rebuild the driver) should you feel like it.

---

