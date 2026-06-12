---
title: "libmysqlclient16-dev"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kernco on 2009-09-02
The package libmysqlclient16-dev has had the description "empty transitional package" for a while now.  Any idea when this is going to become an actual package?

I've been trying to build Amarok from source, and keep getting an error from cmake that it couldn't find the mysqld package.  I think I've tracked the problem to this being an "empty" package.

---

### Post by taavikko on 2009-09-02
> **kernco said:**
> The package libmysqlclient16-dev has had the description "empty transitional package" for a while now.  Any idea when this is going to become an actual package?

I've been trying to build Amarok from source, and keep getting an error from cmake that it couldn't find the mysqld package.  I think I've tracked the problem to this being an "empty" package.

?
```
sudo apt-get build-deb amarok
```

It doesn't depend on libmysqlclient16-dev, it needs libmysqlclient-dev

---

### Post by kernco on 2009-09-02
libmysqlclient-dev is just a metapackage for the most recent version, which is libmysqlclient16-dev.  There's also libmysqlclient15-dev in the repositories, but installing that doesn't fix the problem.

---

