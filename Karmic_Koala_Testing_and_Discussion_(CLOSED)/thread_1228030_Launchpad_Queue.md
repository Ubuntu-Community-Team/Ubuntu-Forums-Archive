---
title: "Launchpad Queue"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andyrogers2008 on 2009-07-31
COuld someone answer this simple question please:-

Why do the uploaded files listed here [Here]("https://launchpad.net/ubuntu/karmic/+queue") sometimes take hours or days to make it into the repo's.

Thanks

Andy

---

### Post by dinxter on 2009-07-31
uploads still have to be built, and on a number of different architectures see [https://launchpad.net/builders/](https://launchpad.net/builders/)

---

### Post by dinxter on 2009-07-31
here's the queue
[https://launchpad.net/ubuntu/+builds?build_text=&build_state=all](https://launchpad.net/ubuntu/+builds?build_text=&build_state=all)

---

### Post by chrisccoulson on 2009-07-31
> **andyrogers2008 said:**
> COuld someone answer this simple question please:-

Why do the uploaded files listed here [Here]("https://launchpad.net/ubuntu/karmic/+queue") sometimes take hours or days to make it into the repo's.

Thanks

Andy

Those are new source packages (or existing source packages introducing new binary packages). The reason that they may sit there for some time is because they have to be approved by an archive admin.

---

