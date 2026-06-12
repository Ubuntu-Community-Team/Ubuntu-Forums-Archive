---
title: "help!! can't upgrade 10.10 to 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by doubleOh on 2011-05-01
Whenever I try to upgrade to 11.04 the process just stops and I haven't been able to access the software center or update manager for some time now( it starts up but closes immediately)
how can i correct this?
thanks :)

---

### Post by mörgæs on 2011-05-01
If your machine is still on 10.10, I would advice you to stay there for now. There are many problems in 11.04.

If you boot the machine and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

does it get healthy again?

---

### Post by doubleOh on 2011-05-03
Ok, i ran the above commands and it just got considerably worse. i can't use my keyboard , my taskbar disappeared and when i restarted it reappeared but now my topscreen bar is gone . i have to keep reconnecting my mouse whenever i restart.
how can i fix this?

---

### Post by mörgæs on 2011-05-03
If these commands do not work, I would reinstall the system. Troubleshooting might take much longer time.

---

### Post by doubleOh on 2011-05-04
thanks. I've opted to reinstall my system.

---

