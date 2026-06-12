---
title: "How to install a certain version of Cacti"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by MatsB on 2006-08-10
How can I choose a certain version of Cacti (0.8.6) to be installed when issue the sudo apt-get install command?

If I use sudo apt-get install cacti i get 0.8.6.h butI want 0.8.g instead.

---

### Post by mlind on 2006-08-10
Dapper seems to only have 0.8.6h-1ubuntu3 available on repositories. If you have multiple versions of same package available, you can install specific version with apt-get/aptitude using 

```

sudo aptitude install package=*version*

```

For cacti 0.8.6h-1ubuntu3
```

sudo aptitude install cacti=0.8.6h-1ubuntu3

```

---

### Post by MatsB on 2006-08-11
I run apt-cache search cacti which only displayed 2 entrys. I guess this the only way to determin which packages are available.

So in other words it's not possiple to install let say cacti 0.8.6g unless it's in Ubuntus repositories with apt-get command.

---

### Post by mlind on 2006-08-11
> **MatsB said:**
> I run apt-cache search cacti which only displayed 2 entrys. I guess this the only way to determin which packages are available.

So in other words it's not possiple to install let say cacti 0.8.6g unless it's in Ubuntus repositories with apt-get command.

If apt-cache sees it then it's on some repository and you can install it with  *aptitude install package=version*.

---

### Post by MatsB on 2006-08-11
Nope apt-cache only sees this:

cacti - Frontend to rrdtool for monitoring systems and services
cacti-cactid - Multi-Threading poller for cacti

Any other ideas how can control which version to install if not listed?

---

### Post by mlind on 2006-08-11
> **MatsB said:**
> Nope apt-cache only sees this:

cacti - Frontend to rrdtool for monitoring systems and services
cacti-cactid - Multi-Threading poller for cacti

Any other ideas how can control which version to install if not listed?

*apt-cache show <package>* lists available versions for that package. If you want to install a local .deb package, then use **dpkg -i /path/to/package.deb**.

Have you found newer version of cacti .deb package somewhere?

---

### Post by MatsB on 2006-08-11
> **mlind said:**
> 
Have you found newer version of cacti .deb package somewhere?

No. I was actually thinking about trying 0.8.6g instead because i'm having a lot of strange things happening when editing anyone of the templates adn saving the change. In some cases i've ended up in dublicate or erased templates :(

---

### Post by mlind on 2006-08-11
> **MatsB said:**
> No. I was actually thinking about trying 0.8.6g instead because i'm having a lot of strange things happening when editing anyone of the templates adn saving the change. In some cases i've ended up in dublicate or erased templates :(

I guess you're out of luck unless you compile it from source package (or sources).

---

