---
title: "loading modules"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by DumDum on 2006-08-09
Hello!

Where can I define options for modules and tell the system the priority of their loading (which one loads first, second, ...)?

On other distribution I remember that there was a file /etc/modules.conf....

thanks!

---

### Post by simonn on 2006-08-09
> **DumDum said:**
> 
Where can I define options for modules 


Create a new file or use an existing file in /etc/modprobe.d and add lines like:

```

options [module] [options...]

```

Have a look at existing files in said directory to get an idea of how it works.

> 
and tell the system the priority of their loading (which one loads first, second, ...)?

On other distribution I remember that there was a file /etc/modules.conf....


It is /etc/modules in Ubuntu.

List the modules and they are loaded in order.

---

