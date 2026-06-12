---
title: "System Update question"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by rockmyway on 2006-11-11
Hello, I've installed Ubuntu 6.06 LTS just past week on my Sony Vaio laptop. As soon as I booted into the system for the first time, ubuntu prescribed around 200 MB of upgrades, which I carried out. But my hard disk space has decreased dramatically. And everytime I upgrade the system files, my hard disk space is decreasing. Could someone please let me know where the installation files are stored so that I can remove them after each upgrade?

Thanks,
me.

---

### Post by lloyd_b on 2006-11-11
Take a look in "/var/cache/apt" (or is it "/var/cache/apt/archives"?).  By default, the system caches all .deb packages there (in case you need to reinstall), and that directory can get mighty big after a while....

Note that if you're using Synaptic, there's a configuration option as to whether it keeps a copy of those files after the installion.  Look under "Settings" to find it.  I'm assuming that there's something similar for other package managers.

Lloyd B.

---

### Post by rockmyway on 2006-11-11
Thanks for the reply. It worked!!

---

