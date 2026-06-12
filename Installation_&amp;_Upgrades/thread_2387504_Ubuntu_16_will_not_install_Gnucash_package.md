---
title: "Ubuntu 16 will not install Gnucash package"
date: 2018-03-19
forum: Installation &amp; Upgrades
---

### Post by selvaswami2 on 2018-03-19
Hi;

This is a standard install -- nothing that isn't in the Package Manager list. But when I got around to installing Gnucash so I could catch up on my business accounting, it refuses to install the package.

Even as root in Terminal, I get this:

E: Malformed entry 1 in list file /etc/apt/sources.list.d/getdeb.list (Component)
E: The list of sources could not be read.
E: Malformed entry 1 in list file /etc/apt/sources.list.d/getdeb.list (Component)
E: The list of sources could not be read.

I would appreciate any advice or help in resolving this.

Thank you,

Selvaswami

---

### Post by oldos2er on 2018-03-19
What does ```
cat /etc/apt/sources.list.d/getdeb.list
``` show?

---

### Post by selvaswami2 on 2018-03-19
Hi;

Never mind -- I went and got getdeb and playdeb, and that put things back in order. GnuCash installed and launched.

Thanks,

Selvaswami

---

### Post by ajgreeny on 2018-03-20
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

