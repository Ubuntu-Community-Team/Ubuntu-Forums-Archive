---
title: "Installed Ubuntu Server and now it says no bootable device."
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by jacobeads1 on 2012-05-11
Hello,

I have a small computer that will be turned into a simple server that runs IP cams. I have installed Ubuntu Server at least 20 times on my hosting company's servers but have never came into this issue.

After the install is completed successfully. It reboots and trys to boot from the drive but says that it cannot boot. I tried it in 2 other machines and it did the same. I **did **install GRUB as well.

This is the newest version of Ubuntu server.

Any ideas?

This machine is running 1 1/2 gigs of ram and a 2.5 GHZ Processor.

Thanks!
Jacob

Thanks
Jacob

---

### Post by darkod on 2012-05-11
Did you set up the boot flag on any partition, for example on the root partition?

I am talking only about the boot flag, not installing grub to the partition. Many boards are used to seek a boot flag that windows uses. Ubuntu doesn't use it so the default ubuntu install never sets a boot flag. The board might think there is no bootable device not finding any boot flag (even though linux doesn't need it).

---

### Post by jacobeads1 on 2012-05-11
Hello,

Thank you for your response!

I checked and the  boot flag is on when I re installed it. It is still doing the same thing.

Thanks
Jacob

---

### Post by darkod on 2012-05-12
Do you have the option to boot the server with the desktop live cd in live mode, and run the boot info script from the link in my signature? It will show many details. Post the results as explained there.

---

