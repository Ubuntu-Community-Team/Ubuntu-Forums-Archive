---
title: "[SOLVED] password expiration, is it possible?"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2007-10-08
Good day everyone! My boss told me to find out some info on this thing, It it possible to make passords expire in say 30 days in Linux? Thank you!

---

### Post by hangthedj on 2007-10-08
```

Usage: passwd [options] [LOGIN]

Options:
  -a, --all                     report password status on all accounts
  -d, --delete                  delete the password for the named account
  -e, --expire                  force expire the password for the named account
  -h, --help                    display this help message and exit
  -k, --keep-tokens             change password only if expired
  -i, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -l, --lock                    lock the named account
  -n, --mindays MIN_DAYS        set minimum number of days before password
                                change to MIN_DAYS
  -q, --quiet                   quiet mode
  -r, --repository REPOSITORY   change password in REPOSITORY repository
  -S, --status                  report password status on the named account
  -u, --unlock                  unlock the named account
  -w, --warndays WARN_DAYS      set expiration warning days to WARN_DAYS
  -x, --maxdays MAX_DAYS        set maximim number of days before password
                                change to MAX_DAYS

```

---

### Post by PryGuy on 2007-10-09
Thanks, pal!

---

