---
title: "Bootchart not working after upgrading to 12.10"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by memristor on 2012-10-21
I am experiencing really bad bootup,login and shutdown times after upgrading to 12.10.
I installed bootchart and pybootchart but they are not working. Here is what the /var/log/upstart/bootchart.log says:

```

bootchart stop/pre-stop, process 394
	pre-stop process 401
/lib/bootchart/gather: 35: cd: can't cd to /var/run/bootchart
/lib/bootchart/gather: 35: cd: can't cd to /var/run/bootchart
bootchart stop/pre-stop, process 389
	pre-stop process 397

```

Any ideas why cd is not working?

---

