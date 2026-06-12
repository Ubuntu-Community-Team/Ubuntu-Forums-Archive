---
title: "[SOLVED] Seahorse segfaults"
date: 2008-09-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by taavikko on 2008-09-05
Can anyone confirm?
[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/265040](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/265040)

---

### Post by ronacc on 2008-09-05
take another look at your report , its already triaged and reported upstream .

---

### Post by taavikko on 2008-09-05
> **ronacc said:**
> take another look at your report , its already triaged and reported upstream .

Thanks, this thread was just to notify if someone else suffers from the same issue.

---

### Post by analystscouch on 2008-09-05
Yeah, this happens for me as well.

---

### Post by Nullack on 2008-09-05
Good stuff - upstream flagged it critical so hopefully itll be fixed before the gnome RC1

---

### Post by taavikko on 2008-09-07
> **Nullack said:**
> Good stuff - upstream flagged it critical so hopefully itll be fixed before the gnome RC1

Outstanding work by devs, fix committed
[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/265040](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/265040)
[http://bugzilla.gnome.org/show_bug.cgi?id=551007](http://bugzilla.gnome.org/show_bug.cgi?id=551007)

---

### Post by excogitation on 2008-09-20
Does it also segfault when you try to "Find remote keys on a keyserver"? (or is it just me?)

```
seahorse
** Message: init gpgme version 1.1.6

** (seahorse:21839): CRITICAL **: update_uids: assertion `SEAHORSE_IS_PGP_SOURCE (source)' failed

** (seahorse:21839): CRITICAL **: calc_validity: assertion `pkey->uids' failed

** (seahorse:21839): CRITICAL **: update_uids: assertion `SEAHORSE_IS_PGP_SOURCE (source)' failed

** (seahorse:21839): CRITICAL **: calc_validity: assertion `pkey->uids' failed

(seahorse:21839): GLib-CRITICAL **: g_utf8_casefold: assertion `str != NULL' failed
Segmentation fault

```

---

### Post by mc4100 on 2008-09-20
On another (sort of related) note, if you fire up seahorse, go to the remote menu, and "Find remote keys...", anyone, who's not segfaulting, else seeing a type in the window name?
Just checking before bugging it.

Edit: To clarify for excogitation, "Find remote keys..." work's fine for me, but again there's a typo.

---

