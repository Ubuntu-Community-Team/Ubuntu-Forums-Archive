---
title: "Can't update or install packages, 18.04"
date: 2018-09-28
forum: Installation &amp; Upgrades
---

### Post by emeraldsnorlax on 2018-09-28
Trying to install OpenVPN from the command line.
Error:

```

emeraldsnorlax@SnorlaxPC:~$ sudo apt-get update
[sudo] password for emeraldsnorlax: 
E: Type &#8216;Executing:&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/mono-official.list
E: The list of sources could not be read.


```
Can't seem to update packages or install any.
There is also this error in the system tray:
[https://imgur.com/a/fz3wzVF](https://imgur.com/a/fz3wzVF)

Any ideas?

---

### Post by oldos2er on 2018-09-28
Fix the error? May we see the contents of /etc/apt/sources.list.d/mono-official.list? ```
cat /etc/apt/sources.list.d/mono-official.list
```

---

