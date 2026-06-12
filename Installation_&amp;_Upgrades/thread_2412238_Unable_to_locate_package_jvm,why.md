---
title: "Unable to locate package jvm,why?"
date: 2019-02-10
forum: Installation &amp; Upgrades
---

### Post by maks88 on 2019-02-10
I am trying to reinstall the open jdk for oracle jdk . 
When i looking for jvm i can find it , but when i trying to remove it with this command :
```

sudo apt-get remove --auto-remove --purge jvm

```

I got this error: 
```

someone@someone-System-Product-Name:~$ sudo find / -name jvm
/usr/lib/debug/usr/lib/jvm
/usr/lib/jvm
/usr/share/gdb/auto-load/usr/lib/jvm
find: ‘/run/user/1000/gvfs’: Permission denied
someone@someone-System-Product-Name:~$ sudo apt-get remove --auto-remove --purge jvm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package jvm

```

Please help ..

---

### Post by CatKiller on 2019-02-10
jvm isn't the name of the package, it's provided by a package. The name of the package will differ depending on which version you were using, and whether you were using the implementation in the normal repositories, or Oracle's one, or whatever.

---

### Post by The Cog on 2019-02-10
In a command prompt, enter the command
```
apt search jdk | less
```
You can see the names of lots of packages. Many merely mention "jdk" in their description (not shown), but a few have jdk in their names. Some will also be marked as installed. Use up/down arrows to view the list.
Then type ```
/jdk
``` and press enter to search for "jdk". 
Q to quit.

---

