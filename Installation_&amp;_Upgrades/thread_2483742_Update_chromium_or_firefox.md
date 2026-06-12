---
title: "Update chromium or firefox"
date: 2023-02-07
forum: Installation &amp; Upgrades
---

### Post by alexlaijin17 on 2023-02-07
On these days, I’ve been trying to update at least my Firefox or chromium in the Ubuntu 12.04.1 because they work so slowly and everything I found was using terminal command sudo apt-get upgrade or update. I tried that but what my console was showing me has nothing to do with what I saw on a few tutorials, can anyone explain why this is isn’t working?


What it shows me:
GLib-Gobject-CRITICAL **: /build/buildd/glib2.0-2.32.3/./gobject/gtype.c:2722: You forgot to call g_type_init()
(process: 2832): GLib-Gobject-CRITICAL
**: g_type_interface_add_prerequisite: assertion 'G_TYPE_IS_INTERFACE (interface_type)' failed

Pd: I suppose my Ubuntu version is pretty old

---

### Post by monkeybrain20122 on 2023-02-07
Ubuntu 12.04? Is it a typo? 12.04 is long dead.

---

### Post by deadflowr on 2023-02-07
> Pd: I suppose my Ubuntu version is pretty old
Yes.
Time to upgrade
It's not worth anyone here's time to help with a very very dead release.

But we will help you navigate to a new release.

---

### Post by TheFu on 2023-02-07
> **deadflowr said:**
> Yes.
Time to upgrade
It's not worth anyone here's time to help with a very very dead release.

But we will help you navigate to a new release.

+1.  Long dead. 

Actually, 12.04 had some issues that only 12.10 corrected. It was serious enough that 12.10 was promoted to LTS ... with support for ending over 5 yrs ago.  I think 12.10 was why Canonical started with HWE kernels (but don't quote me).

---

