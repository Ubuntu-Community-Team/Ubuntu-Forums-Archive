---
title: "After install 10.04 NVidia proprietary driver has to be reinstalled on every reboot"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by wd5gnr on 2010-04-30
Title says it all.

Boot gives me the "Running in low graphics mode" dialog. Switch to a real console, kill kdm, run the NVidia installer, and start kdm. All is great. Next boot, same thing over again.

Any ideas?

---

### Post by wd5gnr on 2010-04-30
Ok, I think I figured it out. The distribution comes with a newer binary driver and was installing it with DKMS. But for some reason I had an old version of the Open GL driver so ksmserver would find a mismatch after DKMS rebuilt the driver. Reinstalling would get the driver and Open GL in sync.

But I never found the "official" package to reinstall to get the matching libOpenGL! Solution was to go get the same version off the NVidia site and install it. Then have to either keep using the NVidia packages or the Ubuntu packages.

---

