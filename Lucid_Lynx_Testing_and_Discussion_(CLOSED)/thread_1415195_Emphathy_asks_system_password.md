---
title: "Emphathy asks system password"
date: 2010-02-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by forcecore on 2010-02-24
why empathy wants system password for log in to account, it should be able to log in without system password.

---

### Post by kurros on 2010-02-24
Is it asking to unlock the gnome keyring?

---

### Post by forcecore on 2010-02-24
yes... but if i want to use it as quest what then???

---

### Post by kurros on 2010-02-24
What do you mean use it as a guest? You need to store the passwords and credentials for the messaging services somewhere. [Gnome Keyring]("http://live.gnome.org/GnomeKeyring") is gnome's secure storage for apps to use.

The gnome keyring should automatically unlock when you log in. If you are using auto login (aren't entering a password) to the desktop then it would not and you would still need to enter the keyring password when something needs it. There might be some workaround to this using PAM or something?

Also remember that the gnome keyring password doesn't have to be the same as the user's login password. Though that is usually what people do I think.

---

### Post by anders_c_ on 2010-02-24
you can totally disable the keyring password.
its under "Accessories->Passwords and Encryption Keys"
just set it to an empty password

---

