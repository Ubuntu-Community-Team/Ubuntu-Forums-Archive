---
title: "Which kernel for Athlon64 but in 32-bit"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by ubuntufans on 2005-06-27
Should i use 686 kernel for 32-bit on Athlon64 machine or K7? or stick with 386?

Thanks guys

---

### Post by dialate on 2005-06-27
Are you running x86-64 Ubuntu now, and want to boot with a 32-bit kernel? I wouldn't recommend it, since all your other packages are compiled for x86-64, and that is bound to cause big problems. I doubt it would boot at all.

If you are installing from scratch with x86 Ubuntu, any of those would work, but I would recommend enabling 32-bit mode in your BIOS settings before you start the install.

---

### Post by ubuntufans on 2005-06-27
[QUOTE=dialate]Are you running x86-64 Ubuntu now, and want to boot with a 32-bit kernel? I wouldn't recommend it, since all your other packages are compiled for x86-64, and that is bound to cause big problems. I doubt it would boot at all.

If you are installing from scratch with x86 Ubuntu, any of those would work, but I would recommend enabling 32-bit mode in your BIOS settings before you start the install.[/QUOTE]

no i install 32-bit version, it comes with 386 kernel, so should i go for 686 or K7 kernel upgrade?

---

### Post by dialate on 2005-06-27
Either one should work fine. If for some strange reason it doesn't, you can always fall back to the 386 kernel by pressing esc when GRUB comes up when you're booting, and choosing it.

---

### Post by dewey on 2005-06-27
K7 is optimized for Athlon chips and above.
686 is optimized for pentiums.

Go with k7.

---

