---
title: "Boot Issue! Help"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by ArchCorsair on 2007-12-10
I am attempting to boot into Ubuntu 7.10 x64 live CD

i tried regular boot and it stalls at:
```

* Checking Battery State                                   [OK]
* Running local boot scripts (/etc/rc.local)               [OK]

```

Then I tried again, adding this to boot parameters:
```

noapic nolapic irqpoll noirqdebug

```

It still stalls at the same spot, help!

[B]_My pc:_
Laptop, hp dv9543cl
2.0 Ghz Duo
2gb ram
2x 160gb HDD[/B]

---

### Post by ArchCorsair on 2007-12-10
The issue was fixed by running this:
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo xstart

```

---

