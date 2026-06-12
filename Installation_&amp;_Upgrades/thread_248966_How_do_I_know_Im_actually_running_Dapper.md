---
title: "How do I know Im actually running Dapper?"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by vulturesrow on 2006-09-01
Yes I really asked that. Ive been away from Ubuntu for a while and was unaware that Dapper had been released. When I used the update manager it informed me that dapper was out but I dont remember asking me if I wanted to updated. It did update a bunch of things but Im not sure what. Is there something I can do to verify the version of Ubuntu I am using now? :confused:

---

### Post by Kingsley on 2006-09-01
system > about ubuntu. it should say in the first paragraph.

---

### Post by taurus on 2006-09-01
You can update from breezy to dapper by editing /etc/apt/sources.list, replacing breezy with dapper in there.  Then,

```

sudo aptitude update
sudo aptitude dist-upgrade

```

---

