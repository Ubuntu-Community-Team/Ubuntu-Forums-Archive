---
title: "grub problem"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by jay941 on 2010-03-22
i have a problem with grub. i installed xp and ubuntu and when done, grub flashes on for about 1 second, then boots to ubuntu. i cannot get to xp at all. anyone know how i can make the grub screen stay on longer so i can choose?

---

### Post by kansasnoob on 2010-03-22
While booted into Ubuntu run this command from Terminal:

```
grub-install -v
```

Then post the output so we know what version of grub you have.

---

### Post by kansasnoob on 2010-03-22
Actually regardless you could just install "startupmanager":

```
sudo apt-get install startupmanager
```

You can then set the timeout in seconds there whether it's grub2 or legacy grub. It will be in System > Administration >

---

### Post by jay941 on 2010-03-22
thanks for the help. unfortunately the computer is at home and i am working out of town so i won't be able to try it until this weekend

---

