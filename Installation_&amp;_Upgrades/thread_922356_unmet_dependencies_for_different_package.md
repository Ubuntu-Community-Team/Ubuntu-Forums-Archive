---
title: "unmet dependencies for different package?"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by robinc on 2008-09-17
Hi everyone.

I'm trying to install ncftp on ubuntu-8.04.1-server-i386 but I'm getting an unmet dependency error for a package that failed to install ages ago.

I tried sudo aptitude cleanup but still the same error


```


robin@darwin:/var/www$ sudo apt-get install ncftp

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  **khtml2png**: Depends: kdelibs4c2a but it is not going to be installed
             Depends: libkonq4 but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).


```

khtml2png is something I tried to install ages ago..hmm..


Interestingly I installed ncftp on another server about 10 minutes before with aptitude and it worked perfectly!

Thanks in advance for your help.

---

### Post by robinc on 2008-09-17
Resolved..
```

wget ftp://130.75.2.22/pub/mirror/linux/debian-mirror/debian/pool/main/n/ncftp/ncftp_3.1.8-1_i386.deb
sudo dpkg -i ncftp_3.1.8-1_i386.deb

```

---

