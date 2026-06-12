---
title: "Update error message."
date: 2013-12-30
forum: Installation &amp; Upgrades
---

### Post by lift_test on 2013-12-30
Tried updating but got this error message:
Failed to fetch [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/pool/main/g/grub-customizer/grub-customizer_4.0.2-0ubuntu1~ppa1p_i386.deb](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/pool/main/g/grub-customizer/grub-customizer_4.0.2-0ubuntu1~ppa1p_i386.deb) 404  Not Found

Should I just untick launchpad or what?

---

### Post by plucky on 2013-12-30
The file it is looking for doesn't exist on the server > grub-customizer_4.0.2-0ubuntu1~ppa1p_i386.deb

See [Here](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/pool/main/g/grub-customizer/)

Have you tried ```
sudo apt-get update
``` to download the index files again before running the upgrade?

---

### Post by lift_test on 2013-12-30
Thanks, that sorted it.  I'll try to mark thread solved.

---

