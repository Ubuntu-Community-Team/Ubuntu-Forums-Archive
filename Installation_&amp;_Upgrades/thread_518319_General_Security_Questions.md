---
title: "General Security Questions"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by cprofitt on 2007-08-05
Can I make my account a non sudo account?

Can I make the root account have a password?

Thanks.

---

### Post by Pumalite on 2007-08-05
I think Ubuntu has been built to specifically not have a root password. I don't think you can have an account as root.

---

### Post by aysiu on 2007-08-05
> **PrivateVoid said:**
> Can I make my account a non sudo account?

Can I make the root account have a password?

Thanks.
Yes, you can do both.

To make your account a non-sudo account, remove yourself from the *admin* group.

To give root a password, type ```
sudo passwd root
``` in the terminal.

To make sure you're making an informed decision, read this first:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Pumalite on 2007-08-05
Learning is a steep curve.

---

