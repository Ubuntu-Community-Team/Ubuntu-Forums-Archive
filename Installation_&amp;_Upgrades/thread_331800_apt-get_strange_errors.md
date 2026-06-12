---
title: "apt-get strange errors"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by jeom01 on 2007-01-05
I have a really strange problem when I try to install packages with apt-get, it just ends with the following error:

```

0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.                  
Need to get 0B/750kB of archives.                                               
After unpacking 4383kB of additional disk space will be used.                   
Do you want to continue [Y/n]? y                                                
E: Waited for /usr/sbin/dpkg-preconfigure --apt || true but it wasn't there     
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true             

```

It doesn't make any differance what package I try to install, it always ends like that, any ideas?

---

### Post by useResa on 2007-01-05
There has been an earlier thread on this problem (see [here](http://www.ubuntuforums.org/showthread.php?t=331507)).

This was resolved by giving the following command
```
 ln -s /bin/bash /bin/sh
```
See post [#14](http://www.ubuntuforums.org/showpost.php?p=1970042&postcount=14).
Maybe this will resolve your problems too.

---

### Post by jeom01 on 2007-01-05
But should I just remove my bash binary? or should I rename it, reinstall bash, and will that remove the link?
Seems like a little strange solution, could I maybe reinstall bash from sources or something?

---

### Post by jeom01 on 2007-01-05
Sorry, my bad, it was the /bin/sh that should be replaced, I tried to rename it and made a symlink to /bin/bash from /bin/sh, however, it didn't help, I still have the same problem.

Should this really help this problem !?

```

xxx@xxx:/bin$ ls -la bash sh                                               
-rwxr-xr-x 1 root root 676836 2006-09-20 00:24 bash                             
lrwxrwxrwx 1 root root      9 2007-01-05 11:27 sh -> /bin/bash                  

```

It didn't work for me anyway, anyone else has any suggestions?

---

