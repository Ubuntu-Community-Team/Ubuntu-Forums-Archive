---
title: "Recent update broke Ubuntu"
date: 2018-10-05
forum: Installation &amp; Upgrades
---

### Post by stefan_ on 2018-10-05
After an automatic update Ubuntu 18.04 hangs on the ramdisk and won´t boot (Loading initial ramdisk...)
I can access the system only if I boot with LIVE CD, also trying to boot an old Kernel won´t work
I tried to regenerate [initrd]("https://linoxide.com/linux-how-to/fixing-broken-initrd-image-linux/") but it did not help
there are currently no further updates for my system (after chroot I ran apt update, apt upgrade)
I added nosplash noquiet nomodeset to grub conf, and ran update-grub
I added my history.log 
Hardware:Intel NUC NUC7i7DNHE BGA 1356 1.9GHz i7-8650U UCFF, BLKNUC7I7DNH2E 

Happy to pay the first one to help a beer via Paypal :-)

Best
Stefan

---

### Post by stefan_ on 2018-10-06
I reinstalled so no help needed anymore

thx

---

