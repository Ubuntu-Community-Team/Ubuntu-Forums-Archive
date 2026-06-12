---
title: "Windows boot menu instead of Grub's"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by wmac on 2008-09-15
Hello,

Previously I was using Wubi to install ubuntu on windows drives. In this way an Ubuntu option is added to "Windows XP OS selection menu".

Now I wanted to use a dedicated partition so I used unetbootin to install Ubuntu. This time I need to select operating system from Grub (instead of XP menu).

Is it possible to have the XP menu instead of Grub (like the one with wubi)?

---

### Post by Partyboi2 on 2008-09-15
Have a look at [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=755782") tutorial

---

### Post by caljohnsmith on 2008-09-15
Yes, you can keep your Windows XP boot menu, and then modify your boot.ini file so that Grub is also an option in the Windows boot menu. That is what the tutorial Partyboi2 aims to achieve, but I think I see some problems in that tutorial. 

I'm curious though, why do you want to keep the Windows XP boot menu instead of simply booting Windows from Grub?

---

