---
title: "Trouble with upgrade - see the error messg."
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by vgunn on 2013-08-21
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/is.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

---

### Post by Bashing-om on 2013-08-21
vgunn; Hi ! Welcome to the forum !

Try this: Terminal codes: (ctl+alt+t yields a terminal)
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

```
which removes the probably invalid database and "apt-get update" repopulates the database with current info.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by vgunn on 2013-08-21
> **Bashing-om said:**
> vgunn; Hi ! Welcome to the forum !

Try this: Terminal codes: (ctl+alt+t yields a terminal)
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

```
which removes the probably invalid database and "apt-get update" repopulates the database with current info.
[INDENT][INDENT]just try'n to help
[/INDENT]
[/INDENT]


... and your help saved me. All seems to be allright!  Thank you so much!.

VGunn

---

### Post by Bashing-om on 2013-08-21
vgunn; Congratulations !

You do good work ... pleased it worked out for us.

Please mark this thread as solved .. as an aid to all from the thread tools menu.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

