---
title: "Update Manager doesn't find update"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by Zegerv on 2011-04-20
Hello,



Normally Update Manager always finds the update to the next version of Ubuntu. It still hasn't given me any notion whatoever. I allready changed the settings from regular to LTS, but nothing changes. There are updates to the kernel, but I cannot download them, so I'm kinda stuck here. If anyone would be so kind to help me in this one? Please try to keep it simple, I'm not really a IT-genius, like you are.


Thanks at forehand,
Zegerv

---

### Post by plucky on 2011-04-20
> Normally Update Manager always finds the update to the next version of Ubuntu

What version are you running?

---

### Post by ezsit on 2011-04-20
The current version of Ubuntu is still 10.10 and the current LTS is still 10.04. If you changed the update settings to notify only new LTS versions, you will not be prompted to upgrade your version of Ubuntu until 12.04 is released. Needless to say, you should still receive regular updates. Updates are quite different from version upgrades.

---

### Post by mörgæs on 2011-04-20
For the regular kernel updates: Try booting the machine and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

If you want to install 11.04, wait a couple of months.

---

### Post by Zegerv on 2011-04-21
Hello,


Oke, thanks a lot, I think I'll just wait a few months.

---

### Post by dino99 on 2011-04-21
sudo gedit /etc/apt/sources.list

changed to natty, then update, that it :)

---

