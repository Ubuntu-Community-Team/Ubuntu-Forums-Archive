---
title: "[SOLVED] cant get gcc to work..."
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by s_raghu20 on 2008-09-17
Hi guys,

Installed a brand new copy of hardy...

tried to run a demo c program.. hello world kind of...
but it turns out that gcc doesnt seem to work here...  It keeps saying...

```
raghav@deskubuntu:~/cprgs$ gcc hello.c -o a.out
hello.c:1:18: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

```

doing a find on the stdio.h all over the system didnt help either...

any pointers ??

thanks in advance..

regards
raghav..

---

### Post by Partyboi2 on 2008-09-17
Have you got build-essential package installed?

---

### Post by s_raghu20 on 2008-09-18
> **Partyboi2 said:**
> Have you got build-essential package installed?

thanks :) it worked.

---

