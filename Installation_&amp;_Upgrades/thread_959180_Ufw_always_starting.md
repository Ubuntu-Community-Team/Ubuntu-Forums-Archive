---
title: "Ufw always starting???"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by tigrezno on 2008-10-26
I've removed several times ufw from init with update-rc.d -f ufw remove
but today it was up again!!

what's this?

also, why services go up when they are updated?

i find it so anoying

---

### Post by Sef on 2008-10-26
How did you install and uninstall it?

---

### Post by tigrezno on 2008-10-26
well, i said it in my post:

/etc/init.d/ufw stop
update-rc.d -f ufw remove

also removed firestarter

---

### Post by tigrezno on 2008-10-27
today it was up again

removing iptables, ufw and firestarer with synaptic is the only way i find to solve it.

is it a bug?

---

