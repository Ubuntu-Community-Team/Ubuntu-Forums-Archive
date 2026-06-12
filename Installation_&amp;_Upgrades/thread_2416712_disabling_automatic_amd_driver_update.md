---
title: "disabling automatic amd driver update"
date: 2019-04-13
forum: Installation &amp; Upgrades
---

### Post by yeetarrel on 2019-04-13
my screen goes black as soon as i install amd drivers. so i have to delete drivers from terminal in order to use onboard (is it?) graphics. And it still updates despite disabling it from softwares and updates section. how can i disable automatic updates?

---

### Post by deadflowr on 2019-04-14
What version of Ubuntu?
What amd driver?

---

### Post by SeijiSensei on 2019-04-15
You can mark as package as "held" which means it won't be updated further.

```
sudo apt-mark hold packagename
```

If the driver is coming from a source outside the repository system, this won't work.

---

