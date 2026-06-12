---
title: "ubuntu studio"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by dhruva023 on 2007-05-10
hi guys,

i want to install ubuntu studio, but i don't have dvd writer.  how can i just jpgrade my feisty  to ubuntu studio?

please help me

thanks

---

### Post by justin whitaker on 2007-05-10
> **dhruva023 said:**
> hi guys,

i want to install ubuntu studio, but i don't have dvd writer.  how can i just jpgrade my feisty  to ubuntu studio?

please help me

thanks

The studio meta packages are up in the repositories. You should be able to get them through aptitude or synaptic.

---

### Post by jjmatt on 2007-05-10
> **justin whitaker said:**
> The studio meta packages are up in the repositories. You should be able to get them through aptitude or synaptic.

You may want to get the latest and greatest ubuntu-studio

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install ubuntustudio-desktop
```

---

### Post by GadgetsGuy on 2007-05-13
YOU GUYS ARE ROCKSTARS !!!! Thank You So Much!

---

