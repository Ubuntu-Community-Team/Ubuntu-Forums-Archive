---
title: "Reset Ubuntu folder permissions.. ?"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by jayarajmohan on 2011-09-02
Hi,

   We are using Ubuntu 10.10 server edition ... Incidently we gave 777 permission for whole server folders, that is we run chmod -R 777 * from / folder...

Now it makes lot of other issues.. We cant even connect server via ssh... 

This is hosted Server, it is any possibility to recover this issue ?

Thanks ...

---

### Post by 2F4U on 2011-09-03
With "recover" you mean revert to the original permissions? If there is a backup you could use that, else it will be difficult. I am not aware of any "rollback" command to revert to the previous state, so you would have to manually set the permissions by hand, which is tedious work.

---

