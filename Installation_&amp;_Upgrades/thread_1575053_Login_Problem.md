---
title: "Login Problem"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by davincidgenius on 2010-09-15
Hi I am really new to Ubuntu. I had installed Ubuntu 10.04 in my Acer Extensa4630Z running Windows7 using Wubi installer. Since then everything was fine. But last week some updates were installed including something called GRUB. Now I cant login to my account. When I go for Ubuntu from the dual boot menu,a black screen appears showing my user account. But the whole thing is freezed, so that i cant even move my cursor to type the password. Can anyone please help me ???

---

### Post by bcbc on 2010-09-15
> **davincidgenius said:**
> Hi I am really new to Ubuntu. I had installed Ubuntu 10.04 in my Acer Extensa4630Z running Windows7 using Wubi installer. Since then everything was fine. But last week some updates were installed including something called GRUB. Now I cant login to my account. When I go for Ubuntu from the dual boot menu,a black screen appears showing my user account. But the whole thing is freezed, so that i cant even move my cursor to type the password. Can anyone please help me ???

It doesn't sound like it's related to the grub update. Have you tried booting a previous kernel, or booting in recovery mode? Any differences doing that?
If you can login using those methods check /var/log/syslog for any exceptions

---

