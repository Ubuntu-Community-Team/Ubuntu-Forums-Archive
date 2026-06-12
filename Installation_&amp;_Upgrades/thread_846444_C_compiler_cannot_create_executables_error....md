---
title: "C compiler cannot create executables error..."
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by spaceba11one on 2008-07-01
I'm trying to upgrade my GTK+ libraries and when I enter ./configure I get this message at the end:

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

What should I do?

---

### Post by sdennie on 2008-07-01
Did you install the C compiler and related build utilites?

```

sudo apt-get install build-essential

```

You are probably going to need a lot more than just that though.  Is there a reason you need to upgrade the GTK libraries?

---

