---
title: "PyGreSQL 4.0"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by placrsaeed on 2009-12-14
Hi All,

I am trying to install[ PyGreSQL 4.0]("http://www.pygresql.org/"). I have installed PostGreSQL 8.4 and have Python 2.6.4 installed.

I keep getting this error when trying to 'build' or 'install' the setup.py file;

"Traceback (most recent call last):
  File "setup.py", line 98, in <module>
    mk_include()
  File "setup.py", line 69, in mk_include
    for f in os.listdir(pg_include_dir_server):
OSError: [Errno 2] No such file or directory: '/usr/include/postgresql/8.4/server'"

I am beginner to Linux, I have Ubuntu Karmic Koala installed. I desperately need to install PyGreSQL and greatly appreciate any assistance.

Saeed.

---

### Post by placrsaeed on 2010-01-13
bump.

Anyone? Please?

---

### Post by hotsnook on 2010-01-15
Experiencing exactly the same issue here.

I would have thought this problem would have bitten more than 2 people.

Awaiting a life line.

---

### Post by hotsnook on 2010-01-15
I can see what is going on now.

The missing path is related to postgresql development package that is not installed :(

The following got past that error:

```
sudo apt-get install postgresql-server-dev-8.4
```

I however have landed in another issue with build failure.

Probably along the same lines. More packages to install probably.

---

### Post by hotsnook on 2010-01-15
Problems solved (for me anyway)

Needed to:
```

$ apt-get install python-dev
$ apt-get install build-essential
```

BEFORE trying:
```

$ sudo easy_install PyGreSQL
```

I am in the process of install turbogears 2.1 on Karmic

---

### Post by placrsaeed on 2010-01-18
It worked for me too.

Your life saver dude.

Thanks for your help. Appreciate it.

---

