---
title: "configuration: No such file or directory"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by SIXAXIS on 2008-02-10
Hi again guys,

I am still trying to install Super Mario War and I've gotten to the package compiler. Everytime I enter "sudo checkinstall" it goes through with it until it comes up with this error:

```
Makefile:13: configuration: No such file or directory
```

What does that error mean and how can I fix it so I can continue my installation of SMW?

---

### Post by Pumalite on 2008-02-10
Do you have build-essential installed?
sudo aptitude install build-essential

---

