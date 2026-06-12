---
title: "Error when trying to use &quot;sudo dpkg-reconfigure locales&quot;"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by D@niel on 2007-05-27
Hello,

an older version of Ubuntu (5.10) is making problems: There are problems with the locale definition files and I was trying to repair them through "sudo dpkg-reconfigure locales", but then "cannot open locale definition file" appears in every line.

I've already searched for solutions, but they don't helped me...

Hope you can help! :)

Greetings,
D@niel

---

### Post by Pragmatist on 2007-05-27
Let's see the permissions:

```
ls -l -d /usr/lib/locale 
```

```
ls -l /usr/lib/locale 
```

---

### Post by D@niel on 2007-05-27
The permissions are:
> drwxr-xr-x 10 root root 4096 May 27 16:52 /usr/lib/locale

List:
> drwxr-xr-x 2 root root 4096 May 27 16:52 en_AU.utf8
drwxr-xr-x 2 root root 4096 May 27 16:52 en_BW.utf8
drwxr-xr-x 2 root root 4096 May 27 16:52 en_CA.utf8
drwxr-xr-x 2 root root 4096 May 27 16:52 en_DK.utf8
drwxr-xr-x 2 root root 4096 May 27 16:52 en_GB.utf8
drwxr-xr-x 2 root root 4096 May 27 16:52 en_HK.utf8
drwxr-xr-x 2 root root 4096 May 27 16:52 en_IE.utf8
drwxr-xr-x 2 root root 4096 May 27 16:52 en_IN


---

