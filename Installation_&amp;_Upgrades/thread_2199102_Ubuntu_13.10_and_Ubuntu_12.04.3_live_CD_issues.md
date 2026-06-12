---
title: "Ubuntu 13.10 and Ubuntu 12.04.3 live CD issues"
date: 2014-01-12
forum: Installation &amp; Upgrades
---

### Post by kwchelchen on 2014-01-12
Hi, 
I was trying Ubuntu 12.04.3 and Ubuntu 13.10 with the following settings and results:

**BIOS settings for Ubuntu 12.04.3:**

Boot mode: Legacy support

Boot Priority: Legacy first

OS optimized defaults: other OS

Secure boot: disabled

Graphic device: tried both, optimus and UMA-only

**Result:**

Try  Ubuntu without installing - Ubuntu started to the language menu, after  choosing a language, the screens stays black...meaning a graphic driver  issue.



**BIOS settings for Ubuntu 13.10:**

Boot mode: UEFI because Ubuntu 13.10 should support UEFI

secure boot: tried both

OS optimized defaults: other OS
Graphic device: tried both, optimus and UMA-only
**Result:**
Try Ubuntu without installing - black screen ...


Any help/ideas?



best regards

Marc

---

### Post by sudodus on 2014-01-12
Welcome to the Ubuntu Forums :-)

You have described the problems quite well, which helps understanding. But ***we need to know about your computer*** too in order to give relevant advice. So please specify

- Brand name and model
- CPU
- RAM
- graphics chip/card
- wifi chip/card

---

### Post by Bucky Ball on 2014-01-12
*Thread moved to **Installation & Upgrades**.*

Welcome. See if nomodeset helps. When you boot to the options 'Try Ubuntu' 'Install Ubuntu' etc., hit F6 and choose 'nomodeset'. Continue and try Ubuntu.

---

### Post by kwchelchen on 2014-01-12
Thanks, the "nomodeset" was the helping hint !!!

---

### Post by Bucky Ball on 2014-01-12
Excellent news! This usually means there are graphics issues but now you can get to a desktop you can continue to use the open-source drivers or investigate how to install the drivers for your graphics card, if you have one. 

If it breaks on reboot, let us know and can show you how to make the nomodeset option permanent.

If thread is solved, please help others by marking it that way using the instructions in the link in my signature. ;)

Enjoy!

---

