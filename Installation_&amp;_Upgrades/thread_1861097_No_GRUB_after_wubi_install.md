---
title: "No GRUB after wubi install"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by frozen99 on 2011-10-15
I need help installing Ubuntu via wubi on my Win7 laptop. Let me explain why I need a wubi install.

I dropped my laptop and now the DVDR drive does not work, at all.

My BIOS doesn't support booting from USB as the laptop originally came with Vista. To update the BIOS, I have to roll back to Vista which I cannot do since I don't have the recovery CD or a disc with Vista on it. 

So here we are with wubi. I had an install of Ubuntu a few months back but had to remove it. I had installed it by CD. Now when I install via wubi, it seems to complete installation correctly. I'm prompted to reboot now or later manually. Either way I do it, when I boot there is no option to boot to Ubuntu (Grub menu doesn't appear). In the past I used a Windows app called Easy BCD to wipe Ubuntu off the Windows Boot manager. I had to use it because of my kids using the laptop while I'm at work. Could Easy BCD be affecting GRUB? Please help

---

### Post by raja.genupula on 2011-10-15
OK i think this link can help you to resolve your issue.

[http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

---

### Post by frozen99 on 2011-10-15
Thank you so much! That is exactly what I was looking for! It worked!

---

### Post by raja.genupula on 2011-10-16
you're welcome!

---

