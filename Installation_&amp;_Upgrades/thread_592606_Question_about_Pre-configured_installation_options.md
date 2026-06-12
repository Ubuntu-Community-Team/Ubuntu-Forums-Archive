---
title: "Question about Pre-configured installation options"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by armon_d on 2007-10-26
It seems to be a highly touted feature that Gusty Server has ~5 pre-configured server options (LAMP, DNS, etc...). BUT, I cannot seem to find any page that actually says what these will install. I want to upgrade my Ubuntu 6.06 install to a 7.10 this weekend, and I have a mail server, file server, dns, and lamp. So, does anyone know exactly what these different "pre-configured" setups actually provide? (In terms of packages)

BTW, Suggestion: Make a Server WIKI page that actually says what these options do, instead of the fact that they exist. Possibly link to it from the Ubuntu Server page. And yes, I have this exact post in the server section too, but I didn't get a response.

---

### Post by armon_d on 2007-10-27
Bump

---

### Post by louieb on 2007-10-27
Runing ```
tasksel --help
```Led me to run ```
 tasksel --list-tasks
```Led me to run  ```
tasksel --task-packages lamp-server
```

Seem to be 25-26 package sets  in all.

---

### Post by armon_d on 2007-10-27
So, is there a way to find out what packages are in each of the preconfigured options? (E.g. is Samba in the file server?)

---

### Post by louieb on 2007-10-27
> **armon_d said:**
> So, is there a way to find ....
:guitar:See my other post Dapper has tasksel too

---

