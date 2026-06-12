---
title: "broke my apt"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by cohoking on 2012-11-15
when I try and update, 

```
sudo apt-get update
```

I get the following message
```

apt-get: error while loading shared libraries: libapt-pkg.so.4.12: cannot open shared object file: No such file or directory

```

Synaptic package manager does't work either. I have no idea what I did but it's completely broken. 

I am looking to reinstall or fix apt, preferably without reinstalling ubuntu completely.

I've looked around and don't see a solution to this problem.

any help appreciated!

Ubuntu 12.04 64, IBM T400

---

### Post by workaround on 2012-11-15
Do reinstall-repair, that should fix the installation.

---

### Post by Lars Noodén on 2012-11-16
Have you tried the following?

```

sudo apt-get --fix-broken --reinstall install libapt-pkg4.12

```

---

### Post by cohoking on 2012-11-19
> **Lars Noodén said:**
> Have you tried the following?

```

sudo apt-get --fix-broken --reinstall install libapt-pkg4.12

```

Sorry this took so long to respond; this doesn't work. Anything involving apt-get returns the same error code as before

```

apt-get: error while loading shared libraries: libapt-pkg.so.4.12: cannot open shared object file: No such file or directory

```

---

### Post by cohoking on 2012-11-19
> **workaround said:**
> Do reinstall-repair, that should fix the installation.

Thanks for the tip; can you point me in the right direction how to reinstall? Does this involve an installation disk or is there a simpler way?

---

### Post by cohoking on 2012-11-24
This is how I resolved it. 

get the library manually here:
[http://packages.ubuntu.com/precise/libapt-pkg4.12](http://packages.ubuntu.com/precise/libapt-pkg4.12)

```

ls -l  /var/lib/dpkg/info/libapt-pkg4.12:amd64*
sudo rm -r /var/lib/dpkg/info/libapt-pkg4.12:amd64.postinst
sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_amd64.deb
apt-get install -f

```

I hope this is helpful to others!

---

