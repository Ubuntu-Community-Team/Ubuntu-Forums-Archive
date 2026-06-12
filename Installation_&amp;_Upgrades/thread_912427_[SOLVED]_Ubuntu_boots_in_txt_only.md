---
title: "[SOLVED] Ubuntu boots in txt only"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by alek01 on 2008-09-06
Hi,
I have overstretched my Ubuntu skills when installing the Nvidia driver on my Hardy Ubuntu and I messed-up my installation. after many hours Nvidia works fine:), thank you, but I have various Kernels on the Grub. When I boot the computer everything is OK but I get to Ubuntu Hardy in text mode and need to first login in text mode and then launch X with "startx".
I have two questions:
1)What do I need to do to obtain the "usual" seamless graphical boot mode?
2)How do I get rid of the Kernels that I don't need? (Erasing them form the Grub is easy, I want to remove them from my machine.
Thank you very much for your help 'cause the bleak weather here, I'd like to see the light of day...
Thks:)

---

### Post by ~LoKe on 2008-09-06
Sounds like you disabled GDM?

To remove the kernels, you can simply do...
```
sudo dpkg -r linux-image<blah>
```

I suggest you keep the one previous to your current kernel, in case you need to fall back to it.

---

### Post by alek01 on 2008-09-06
Thnks for the swift reply. I got the name from the Grub menu file and seems to work. Would you know how to "auto start" X prior to to loggin in?
Thank you

---

