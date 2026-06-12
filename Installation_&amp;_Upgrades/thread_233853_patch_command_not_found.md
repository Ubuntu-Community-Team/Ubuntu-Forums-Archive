---
title: "patch command not found"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by MatsB on 2006-08-10
I'm trying to install a patch for Cacti but i'm only getting this:
admin@cacti:/usr/share/cacti/site$patch -p1 -N < fix_search_session_clear_issue.patch
-bash: patch: command not found

---

### Post by mlind on 2006-08-10
If you're going to build that package later, install package called **build-essential** which should also provide **patch** package. 
(If you just need patch binary, install package called patch).

For build-essential (provides patch and build tools)
```

sudo aptitude install build-essential

```

If you just need **patch**
```

sudo aptitude install patch

```

---

