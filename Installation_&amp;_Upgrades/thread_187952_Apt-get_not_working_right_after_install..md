---
title: "Apt-get not working right after install."
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by otakuj462 on 2006-06-03
Hi, the apt-get utility isn't working for certain packages. I'm trying to configure an old computer to act as an ftp server. As such, I switched to root and did:

```
apt-get update
```

This executed fine. I then tried the following two commands:

```

apt-get install ftpd

```


```

apt-get install ftpd

```

But to both of them I got an error message like this one:

```

E: Couldn't find package ftpd

```

I then tried using apt-get to get ssh, and it worked fine. I then set up my ssh server and was able to log in from a local computer.

Could someone please explain to me why this might be happening? Thanks.

-Jake

---

### Post by meng on 2006-06-03
I think you need to enable repositories, specifically universe.
apt-get needs to know where to look for the packages. Some like ssh are standard. Others like ftpd are in expanded repositories.
If you cat /etc/apt/sources/.list it will tell you which repositories are enabled. You can post this if you need more help.

---

