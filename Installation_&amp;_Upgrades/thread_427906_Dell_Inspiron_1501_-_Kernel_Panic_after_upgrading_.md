---
title: "Dell Inspiron 1501 - Kernel Panic after upgrading to Feisty"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by jlapier on 2007-04-29
Just ran the upgrade to Feisty via the update manager on my Dell Inspiron 1501 and now when I boot, it hangs - the screen freezes and the caps-lock and scroll-lock lights start blinking. I tried hitting CTRL-ALT-F4 before it hangs so I can see the messages before it locks up, and it says:
```

Code: Bad RIP value.
RIP [<0000000000000>]
 RSP <fffffffff805c0ca0]
CR2: 0000000000000
  <0>Kernel panic - not syncing: Aiee, killing interrupt handler!

```

Any suggestions? It took a couple hours to upgrade, I'd hate to try to reinstall, but that's the only thing I can think to do. I'd just hate to go through a reinstall and end up with the same problem again.

- Jason L.

---

### Post by jlapier on 2007-04-30
Well, this seemed doomed, so I booted the FF Live CD, mounted my hard drive, backed up my Home directory to a network share, and did a clean install of Feisty. Now I'm working okay. 

Pretty decent site I came across about running Ubuntu on the 1501's: [http://ubuntu1501.blogspot.com](http://ubuntu1501.blogspot.com)

- Jason L.

---

