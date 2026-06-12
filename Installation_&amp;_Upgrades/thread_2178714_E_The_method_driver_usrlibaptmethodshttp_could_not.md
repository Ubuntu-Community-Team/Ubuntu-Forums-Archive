---
title: "E: The method driver /usr/lib/apt/methods/http could not be found."
date: 2013-10-04
forum: Installation &amp; Upgrades
---

### Post by ryan_coplea on 2013-10-04
I'm not really sure what I did to mess this up but I just went to update and I got this message
E: The method driver /usr/lib/apt/methods/http could not be found.
Any help would be appreciated

---

### Post by Bashing-om on 2013-10-04
ryan_coplea; Hi !

As a start, does that file exist ?
```

ls -la /usr/lib/apt/methods/http

```
It should:
> 
sysop@1304mini:~$ ls -la /usr/lib/apt/methods/http
-rwxr-xr-x 1 root root 68928 Sep  4 18:18 /usr/lib/apt/methods/http
sysop@1304mini:~$



[INDENT][INDENT]what,where, who, and why - when- always applies[/INDENT][/INDENT]

---

