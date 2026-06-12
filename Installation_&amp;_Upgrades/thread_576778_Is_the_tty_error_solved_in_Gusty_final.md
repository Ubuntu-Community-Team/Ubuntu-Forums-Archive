---
title: "Is the tty error solved in Gusty final?"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by r3r3 on 2007-10-15
Hello, just wondering if this /bin/sh: can't access tty; job control turned off problem is fixed? Because i tryed the gusty beta and it was still here

---

### Post by Pumalite on 2007-10-15
Maybe what you need is an Alternate CD or a lighter Desktop. What are your specs?

---

### Post by r3r3 on 2007-10-16
my specs aer:

Asus p5b deluxe wifi
C2D 6320
8800 gts 320
Audigy ZS
promise fasttrack s150 sx4 with raid 5
2GB ocz platinum pc2-6400
Raptor 75 gb

i tried the alternate cd with gusty tribe 3, 4, 5 without luck, guess i ll wait the release of gusty final and try :)

---

### Post by Pumalite on 2007-10-16
Alternate CD Installation and at the end of installation, this:

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver
__________________

---

### Post by r3r3 on 2007-10-23
Ok it's working! The problems were my raid5 promise fasttrack s150 sx4 not handled by gusty and a stupid 3 months old NEC (sony) dvdr drive that were doing faulty cds/dvds!

Thanks anyway!

---

