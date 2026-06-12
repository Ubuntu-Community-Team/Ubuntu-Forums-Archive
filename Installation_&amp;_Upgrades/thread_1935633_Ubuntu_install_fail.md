---
title: "Ubuntu install fail?"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by PoLoMoTo on 2012-03-04
I was installing Ubuntu and suddenly the screen went blank, waited a few minutes, checked if the HDD was spinning, then held the power button. Ubuntu showed back up but everything was messed up, held the power button again and it shut off. Rebooted and it went into the windows boot manager not GRUB. Did Ubuntu fail?

---

### Post by darkod on 2012-03-04
Looks like it didn't finish the install. It installs the bootloader at the end of the process so that's why you still have windows bootloader which loaded windows directly.

Depending when was the install stopped, it's not easy to know in what state it is. Probably it's best to do another install but be careful because linux doesn't install onto the same partitions by default. You have to tell it to use the same partitions if they were created correctly.

Or boot into live mode, delete the linux partitions, and start another install.

---

### Post by PoLoMoTo on 2012-03-04
It was installing to unallocated space I created but I didn't tell it too.  It divided that into two partitions half the size.  I was installing from a Live USB drive

---

### Post by darkod on 2012-03-04
What do you mean you didn't tell it to?

You probably use "side by side" option and that installs into an unallocated space it can find. Another option is Something Else, the manual mode which gives you best control of partitions and their sizes.

---

### Post by PoLoMoTo on 2012-03-04
No I clicked install alongside windows and it just started installing

---

