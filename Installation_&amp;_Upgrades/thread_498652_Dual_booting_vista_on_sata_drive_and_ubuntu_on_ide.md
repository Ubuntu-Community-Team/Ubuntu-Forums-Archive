---
title: "Dual booting vista on sata drive and ubuntu on ide drive"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by Edache on 2007-07-11
Hello all, Iam trying to dual boot vista with Ubuntu. I have vista on a 160gig sata drive and I have a 30 gig ide drive I would like to put Ubuntu on, any suggestion?.

---

### Post by gizmoarena on 2007-07-11
Download Easy BCD 1.6. search it on google. It'll save your life ;)
Install Ubuntu on your IDE drive. 
Boot from your primary drive, which is Vista.
Use BCD to install Vista boot loader.

For detailed step by step process, you must visit this tutorial. but remember this tutorial is for one hard disk installation. You have two.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by confused57 on 2007-07-11
Easy BCD is a great option, but you could also consider this:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

either way should work OK, least you have a choice.

---

### Post by Edache on 2007-07-11
Thank you both for your help, Giz I was able to get it to dual boot by installing to the completely empty IDE drive, now I have Grub loading and showing me Ubuntu and Vista for boot options. Again much Thanks. :guitar:

---

