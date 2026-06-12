---
title: "Two versions of mysql?"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by forzagrifo on 2007-09-01
I'm using Dapper and have Mysql 5.0.22 installed and I want to also install the latest version 5.0.45 on the same machine.  Is it possible to have 2 versions on the same machine and use either one as I wish?

Also, if I want to simply upgrade to 5.0.45 and compile it from source, can I simply overwrite the old  5.0.22? Any problems doing this? Or do I need to first uninstall 5.0.22 completely before compiling source for 5.0.45?

TIA

---

### Post by Martje_001 on 2007-09-01
No it's not possible, as they use the same database.

---

### Post by forzagrifo on 2007-09-01
> **Martje_001 said:**
> No it's not possible, as they use the same database.

Thx.  How about upgrading? Can I simply compile from source and it will overwrite the old version? Or do I have to first uninstall the old version (by using Synaptics)?

---

### Post by Martje_001 on 2007-09-01
I prefer upgrading via Synaptic, but if you want to, you can do it directly from the source ;). But, make a backup!

---

### Post by forzagrifo on 2007-09-01
I cannot upgrade in Synaptics because 5.0.45 is not in the repos.  I can only do it from source.  But should I uninstall the old version first?

---

### Post by Martje_001 on 2007-09-01
> **forzagrifo said:**
> I cannot upgrade in Synaptics because 5.0.45 is not in the repos.  I can only do it from source.  But should I uninstall the old version first?

You don't have to, but it's saver if you do, and you don't mind data loss,

---

### Post by forzagrifo on 2007-09-01
thx.  Much appreciated.

---

