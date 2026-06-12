---
title: "From 32bit to 64bit without complete reinstall?"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by Schuttwegraeumer on 2008-05-23
Is it possible to upgrade an 32bit Ubuntu to a 64bit Ubuntu without a complete new installation?

---

### Post by logos34 on 2008-05-23
unfortunately, no.

---

### Post by Schuttwegraeumer on 2008-05-23
Ok, it should work to save the home Dir and delete all other and install Ubuntu new.
Is there a way to save all the installed packages as a list that can be imported?

---

### Post by logos34 on 2008-05-23
> **Schuttwegraeumer said:**
> Ok, it should work to save the home Dir and delete all other and install Ubuntu new.
Is there a way to save all the installed packages as a list that can be imported?

dpkg --get-selections

or

synaptic>file>generate pkg download script

Never tried to import across architectures, though.

---

