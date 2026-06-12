---
title: "upgrade to edgy, old kernel doesn't boot"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by Feb29 on 2007-04-02
I have both kernel 2.4 and 2.6 in my computer,
they both worked till I upgraded my 2.6(dapper) to edgy few days ago.
when I boot kernel 2.4.26, it says:

FATAL: kernel too old
kernel panic: Attempted to kill init!

I recompiled it again under edgy, and installed modutils(2.4.27),
still the same error.

also, I get the error message from modprobe.modutils:modprobe:
QM_MODULES: Function not implemented

Can it be possible that the modutils doesn't support kernel-2.4.26 anymore?

thanks.

---

### Post by zvacet on 2007-04-03
Massage told you all.Why do you need 2.4 kernel?

---

### Post by Feb29 on 2007-04-04
But who gives the message?
i searched the sentence ' too old...', found it neither in kernel source
nor in boot scripts.

maybe glibc-2.4?

for some reason, i still need kernel-2.4 by some older applications and developments

:(

---

