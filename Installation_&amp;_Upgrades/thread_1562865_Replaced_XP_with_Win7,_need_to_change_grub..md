---
title: "Replaced XP with Win7, need to change grub."
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2010-08-28
I'm hoping this will be simple. 

I had XP Home on my dual boot Ubuntu 10.04 LTS amd64 PC & now installed Window 7 Home Premium 64-bit over old XP. Before installing Win7, as a precaution, I disconnected the hard drive where Ubuntu is installed. Now, naturally, the startup screen (grub?) still offers XP. Is there an easy way to re-detect & rewrite the startup menu with the Ubuntu install CD without re-installing Ubuntu 10.04 LTS amd64 again, like a GRUB repair or rewrite?

Thanks.

---

### Post by GARoss on 2010-08-28
Just for kicks, I selected Windows XP Home from the old startup menu &, surprise, Windows 7 booted! Prior to this I installed gparted & checked the info on the Win7 HDD; then read the GRUB list. It listed Windows XP Home but this info matched the info in gparted for Windows 7. So, same is the same.

I realize everything is working but will there be an issue to change the wording in GRUB from Windows XP Home to Windows 7?

---

### Post by GARoss on 2010-08-28
This was simple. I installed *StartUp Manager* from the *Ubuntu Software Center* & ran it in the terminal. It basically detected changes & rewrote itself. :D

---

