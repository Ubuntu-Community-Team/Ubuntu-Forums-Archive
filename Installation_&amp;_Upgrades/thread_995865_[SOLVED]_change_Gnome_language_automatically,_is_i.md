---
title: "[SOLVED] change Gnome language automatically, is it possible?"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2008-11-28
Good day everyone!
I install Ubuntu on multiple machines and what I do is I install Ubuntu from the installation CD, then I install additional packages from my postinstall specially customized APTonCD that installs packages and configures system. DVD is not acceptable for some machines so I have to do it this way. I install language packs but I still have to choose default language manually, and it sucks! :( What I want is to make Gnome speak Russian (in my case) after reboot. Do you have any idea how to make it?

Thanks in advance!

---

### Post by PryGuy on 2008-11-28
okay, okay, I got it:
```
sudo sed -i 's/en_US/ru_RU/' /etc/default/locale
```
does the trick (in my case with Russian).

---

