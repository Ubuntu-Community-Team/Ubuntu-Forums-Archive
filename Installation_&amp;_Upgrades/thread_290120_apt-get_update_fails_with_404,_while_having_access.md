---
title: "apt-get update fails with 404, while having access to that file"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Xnor on 2006-10-31
Hello!

I was installing Edgy Eft two days ago and everything went very well until now. Since yesterday apt-get update refuses to get the package lists: 
```

Ign http://security.ubuntu.com edgy-security Release.gpg
Ign http://archive.ubuntu.com edgy Release.gpg
Ign http://archive.ubuntu.com edgy/main Translation-en_US
[...]
Err http://archive.ubuntu.com edgy/main Sources
  404 Not Found
Err http://archive.ubuntu.com edgy/restricted Sources
  404 Not Found
Err http://archive.ubuntu.com edgy/universe Sources
  404 Not Found
[...]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz  404 Not Found
[...]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

While 
```

wget http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz 
```
works, and gets that Sources.gz

The sources.list file should be ok, since I was trying to replace it with one known good example from the forums. 
Can you help me please?

yours

Xnor

---

### Post by Xnor on 2006-10-31
Hi!

Problem solved! 
/etc/apt/apt.conf contained:

```

Acquire::http::Proxy "http://x.x.x.x/";

```

The x.x.x.x stands for our proxy, this proxy has some restrictions set up. 
So commenting out that above line, using direct connection, everything works again. 

Bye!

Xnor

---

