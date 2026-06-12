---
title: "Crashed while upgrading to 14.04. No login on terminal possible."
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by thiemo-weiss on 2014-04-25
Hi there,

While upgrading I unfortunatly confirmed the question about stopping kdm service. After that the system rebooted. Now I can't login on terminals, because no password prompt is shown. Graphical login doesn't work because no WM starts up correctly.

How can I proceed with my upgrade?

Thanks
Thiemo

---

### Post by thiemo-weiss on 2014-04-26
In recovery mode I can do this:

```
# adduser tw
OK
# adduser tw sudo
OK
# passwd tw
Segmentation fault
```

After entering "passwd tw" there is definitly no prompt to enter any new password.

---

### Post by thiemo-weiss on 2014-04-26
I solved the passwd problem with finishing the upgrade in recovery mode:

apt-get -f install

---

