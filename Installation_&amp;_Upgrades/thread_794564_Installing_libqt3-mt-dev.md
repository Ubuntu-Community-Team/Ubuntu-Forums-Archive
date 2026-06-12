---
title: "Installing libqt3-mt-dev"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by pbritocruz on 2008-05-14
Hi,

i'm working on dapper distro and need to install libqt3-mt-dev which depends on a whole big list of other libraries.

when trying to install some of these libraries I got to a cyclic dependency which i don't know how to deal with.

x11proto-xext-dev

depends on

libxi-dev

which depends on

libxext-dev

which depends on 

x11proto-xext-dev (here starts the cycle)


Does anyone know how to deal with this?

Thanks in advance

P

---

